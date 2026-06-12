---
title: "C programming question"
date: 2005-11-17
forum: General Help
---

### Post by funkenstein on 2005-11-17
First off, thanks for reading this...

I'm trying to benchmark some c software that I'm writing - specifically, it's a sort of IDS (intrusion detection system). Right now it's something along the lines of:
```

::some code::

time( &start );

function ( var1, var2 ){
code snippet
}

time( &end );

benchmark = ( end - start );

printf( "%d" , benchmark );
::some code::

```

Thing is, time() returns in miliseconds and I need microseconds: Right now it's returning 0 every time. Any ideas on how to go about it?

I've looked at [http://www.ittc.ku.edu/utime/](http://www.ittc.ku.edu/utime/) but I don't know how to enable CONFIG_UTIME, nor how to use it in my source code thereafter.... nor, as a matter of face, if it will harm my machine at all...
Please comment with any bit of useful information as I'm really stranded here...
Thanks.

---

### Post by joshuaxls on 2005-11-17
I can't answer your question, but I know a few things...

First off, I have done some benchmarking before and the code I used to benchmark was different. I used times(), which is defined in <sys/times.h>. times() takes a pointer to a buffer of type **struct tms** as its argument, and it fills this buffer with information about user and system CPU time taken by the current process. You probably don't want this, but times() also **returns** a value of type **clock_t** which is the number of clock ticks since system boot up. So if you call times() before and after your code, supplying a dummy buffer as an argument but storing the return value in two unique variables, you can get a better idea of how many milliseconds it took. The code looks something like this:

```
#include <sys/times.h>
#include <time.h>

clock_t start, end;
struct tms dummy;

start = times( &dummy );

*** YOUR CODE ***

end = times( &dummy );

printf( "Elapsed time is %.5f seconds.\n",
   ((double) end - start)) / ((double) CLK_TCK) );
```

CLK_TCK is a constant which defines the number of ticks per second for your architecture. If you don't know, a clock tick is a timer interrupt -- the kernel programs a timer to interrupt the operating system so many times a second (usually 100 or 1000) so that the kernel can take control and take care of system stuff.

I don't think there is any way to get microsecond resolution without using the utime patch. I think I may understand why. Inside of the kernel, two types of time are kept: the number of clock ticks since system boot, and the wall time (which contains milli- and microseconds). However, I think that the standard kernel only makes the number of clock ticks available to userspace and does not provide an interface to get the wall time. Therefore, the kernel would need to be hacked and an extra system call would need to be added (or an existing system call would need to be modified).

Does that make sense? Hope it helps.

---

