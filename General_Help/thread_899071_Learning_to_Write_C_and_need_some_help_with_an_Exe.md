---
title: "Learning to Write C and need some help with an Exercise from my book."
date: 2008-08-24
forum: General Help
---

### Post by Tanjer1588 on 2008-08-24
i picked up a book on the basics of writeing in C and one of the first programs they teach you is basic input output program for copying text

```

#include <stdio.h>

main()
{
     int c;

     while ((c = getchar()) != EOF)
          putchar(c);
}


```

Ok so it gives me two exercise to do with this at the end of the reading for it

1. Verify that the expression getchar() != EOF is 0 or 1.
2. Write a program to print the value of EOF.

Now im totaly stumped on this, the begining of the book says it's helpful to have some one around that knows C and i got you guys and amanda but amandas not here right now :P so i thought i would ask you guys. #1 is real hard cus i have no idea where i would start. #2 is not as hard and i have tryed some ideas but have not figured it out yet. So can some one give me a hand. Im not looking just for an anwser but maybe a way to find one.

thanks so much.

---

### Post by LateNiteTV on 2008-08-24
> **Tanjer1588 said:**
> i picked up a book on the basics of writeing in C and one of the first programs they teach you is basic input output program for copying text

```

#include <stdio.h>

main()
{
     int c;

     while ((c = getchar()) != EOF)
          putchar(c);
}


```

Ok so it gives me two exercise to do with this at the end of the reading for it

1. Verify that the expression getchar() != EOF is 0 or 1.
2. Write a program to print the value of EOF.

Now im totaly stumped on this, the begining of the book says it's helpful to have some one around that knows C and i got you guys and amanda but amandas not here right now :P so i thought i would ask you guys. #1 is real hard cus i have no idea where i would start. #2 is not as hard and i have tryed some ideas but have not figured it out yet. So can some one give me a hand. Im not looking just for an anwser but maybe a way to find one.

thanks so much.

```
if getchar() == EOF
     printf("0\n");
else
     printf("1\n");
```

---

### Post by Tanjer1588 on 2008-08-24
> **LateNiteTV said:**
> ```
if getchar() == EOF
     printf("0\n");
else
     printf("1\n");
```

How would i place that in there? in what space?

---

### Post by LateNiteTV on 2008-08-24
you need to define what EOF is before anything can happen.

---

### Post by Tanjer1588 on 2008-08-24
ok i will work on it, thank you

---

### Post by kjohansen on 2008-08-24
EOF is declared in the stdio header.

for part 1 it will always be a 0 or a 1 because it is a boolean expression, it can either be true or it can be false.  (true=1, false=0)

```

#include <stdio.h>

main()
{
     int c;

     while ((c = getchar()) != EOF)
          putchar(c);
     printf(EOF);
}

```

---

### Post by herewego on 2008-12-10
I'm reading the same book and having the same problem with the 2 questions.  For the second question, my initial idea was as in the post above, however when I run that code I get the following:

```
warning: passing argument 1 of ‘printf’ makes pointer from integer without a cast
```

The book is "The C Programming Language" by Kernighan and Ritchie (I have a link to an online version of the book but was unsure whether it was ok to post) and these 2 questions seem to be common questions answered on the internet but not necessarily in a way that follows from the what has been taught in the book.

Any more thoughts on these 2 questions?

ps I was unsure whether to start a new post or just try and bring this back to life.  Is there an etiquette for this?

Cheers

---

### Post by mdurham on 2008-12-10
EOF must be an int (not a bool) as it's returned by int getchar(), therefore > printf("%d", EOF) will print the value of EOF.

---

### Post by herewego on 2008-12-10
Cool that makes sense.  Still slightly confused about the first question but will keep playing around til it makes sense.

---

### Post by mdurham on 2008-12-10
> 1. Verify that the expression getchar() != EOF is 0 or 1.
That's not really a correct thing to do because the expression '!=' returns a boolean value true of false.

---

