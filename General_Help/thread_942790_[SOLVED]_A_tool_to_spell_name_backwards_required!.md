---
title: "[SOLVED] A tool to spell name backwards required!"
date: 2008-10-09
forum: General Help
---

### Post by Rytron on 2008-10-09
Hi,
Does anyone know of a perl script / online tool / other method(s) to input someone's name and get the reverse of it?

i.e. john doe would be turned into eod nhoj

Thanks.

---

### Post by jespdj on 2008-10-09
Here's a small Python program:
[php]#!/usr/bin/env python
s = raw_input('What is your name? ')
print s[::-1][/php]
Save it in a file named reverse.py, then make it executable:
```
sudo u+x reverse.py
```
And then run it:
```
./reverse.py
```

---

### Post by TheLions on 2008-10-09
in C:

```
#include <stdio.h>
#include <string.h>

int main (void)
{
	char name[100], surname[100];
	int i=0;
		scanf("%s %s",name,surname);
		
		
				
	for(i=strlen(name);i!=-1;i--)
		printf("%c",name[i]);	
	
	printf(" ");
		
	for(i=strlen(surname);i!=-1;i--)
	printf("%c",surname[i]);

return 0;	
	}

```

---

### Post by LowSky on 2008-10-09
> **Rytron said:**
> 
i.e. john doe would be turned into eod nhon

actually it's

eod nhoj

...lol

---

### Post by Seq on 2008-10-09
```
echo "John Doe" | rev
```

[:)]("http://www.google.com/search?q=bash+reverse+string&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")

---

### Post by Rytron on 2008-10-09
> **LowSky said:**
> actually it's

eod nhoj

...lol

:)
Thanks for pointing that out.

---

### Post by Rytron on 2008-10-09
> **Seq said:**
> ```
echo "John Doe" | rev
```

[:)]("http://www.google.com/search?q=bash+reverse+string&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")

Excellent - so simple yet does the job perfectly.

:popcorn:

---

### Post by Idefix82 on 2008-10-09
To add to Seq's solution: just type
```
rev
```
and now type each line that you want to be reversed. When you are done press Ctrl+D.

---

