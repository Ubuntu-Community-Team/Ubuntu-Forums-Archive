---
title: "'tm' undeclared???"
date: 2008-11-02
forum: General Help
---

### Post by naturewhite on 2008-11-02
I'm a beginner in ubutu and got problem while learning c programing under ubuntu environment:
i typed the text below:
#include<time.h>
#include<stdio.h>
#include<stdlib.h>

main()
{
struct tm *tm_ptr;
time_t the_time;

(void)time(&the_time);

printf("Raw time is %ld\n",the_time);
printf("Mytime show:\n");
printf("Date:%02d/%02d/%02d\n",
tm_ptr->tm_year,tm->ptr->tm_mon+1,tm_ptr->tm_mday);
printf("Time:%02d/%02d/%02d\n",
tm_ptr->tm_hour,tm_ptr->tm_min,tm_ptr->tm_sec);
exit(0);
}
and use the command : cc -o mygmtime mygmtime.c
and error apeared:
miss@miss-laptop:~/prog$ cc -o mygmtime mygmtime.c
mygmtime.c: In function ‘main’:
mygmtime.c:15: error: ‘tm’ undeclared (first use in this function)
mygmtime.c:15: error: (Each undeclared identifier is reported only once
mygmtime.c:15: error: for each function it appears in.)
miss@miss-laptop:~/prog$ 

hope someone can help me solve the problem, thanks~

---

### Post by mali2297 on 2008-11-02
You've written tm->ptr instead of tm_ptr at one place, which caused the error.

To get a useful result you also need to assign tm_ptr, for example through the function localtime ().

```

#include <time.h>
#include <stdio.h>
#include <stdlib.h>

int main()
{
  struct tm *tm_ptr;
  time_t the_time;
  
  (void) time (&the_time);
  tm_ptr = localtime (&the_time);

  printf("Raw time is %ld\n",the_time);
  printf("Mytime show:\n");
  printf("Date:%02d/%02d/%02d\n",
         tm_ptr->tm_year+1900,[color=red]tm_ptr[/color]->tm_mon+1,tm_ptr->tm_mday);
  printf("Time:%02d/%02d/%02d\n",
         tm_ptr->tm_hour,tm_ptr->tm_min,tm_ptr->tm_sec);
  return 0;
}

```

---

