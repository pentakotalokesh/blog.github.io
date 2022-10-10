---
title: "Datalink Layer Framing Methods"
date: 2022-10-11T00:39:57+05:30
draft: true
---
Implementation of Bitstuffing in C
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void Bitstuff(char *frame)
{
	int count = 0, j = 0;
	char stuffedframe[100];
	for (int i = 0; i < strlen(frame); ++i, ++j)
	{
		if (frame[i] == '1')
		{
			count++;
			if (count == 5)
			{
				stuffedframe[j++] = '0';
				i++;
			}
		}
		else
		{
			count = 0;
		}

		stuffedframe[j] = frame[i];
	}

	printf("stuffedframe:\n");
	printf("%s", stuffedframe);
}

int main()
{
	char data[20];
	printf("Enter Frame data:");
	gets(data);

	Bitstuff(data);
	return 0;
}
```
#### OUTPUT
```c
Enter Frame data:11111
stuffedframe:
111110
```
