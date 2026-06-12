---
title: "Is my ubuntu install 32 or 64 bit?"
date: 2008-10-03
forum: General Help
---

### Post by zorkerz on 2008-10-03
Unfortunately this has turned out to be a hard question to search for because I am always lead to places discussing which to use not which I already am using. 

I believe I installed a 64 bit ubuntu 8.04 variant but the virtualbox package I needed to install has me second guessing. 

Is there any way to verify if I am using 64 or 32 bit ubuntu?
I checked the about ubuntu (system->about ubuntu) but it does not mention this which is unfortunate.

---

### Post by Calmatory on 2008-10-03
uname -a could show this. Not sure though. :p

---

### Post by Idefix82 on 2008-10-03
Yes, it does show it. If you type
```
uname -a
```
and there is something saying x86_64 then it's 64 bit, otherwise 32.

---

### Post by hyper_ch on 2008-10-03
I think it's
```

uname -i

```

---

### Post by zorkerz on 2008-10-03
If I am correct this gives the kernel version?
here is mine 

> Linux COMPUTER NAME 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

So I guess the i686 is the important part here, however, I don't really understand how this works or how it might translate into 64 or 32 bit.

---

### Post by Ryadt on 2008-10-03
i686 is 32bits

---

### Post by zorkerz on 2008-10-03
uname -i returns 'unknown'

what in gods name does that mean?

Im looking all all the different uname options uname -p which is for my processor also returns unknown.

That answer kinda scares me. My processor is know by me fortunately. Its an intel core2duo 2.12 ghz.

Anyone know whats going on here.

---

### Post by Idefix82 on 2008-10-03
Same here. I wouldn't worry about it, it's probably a glitch in the uname program. If you open the System Monitor it should show you your CPU correctly.

---

### Post by zorkerz on 2008-10-03
you are right Idefix82 system monitor does correctly recognize my processor. This still does not help me in knowing if im using a 64 or 32 bit install. The more I read about i686 it makes me think its not a 64 bit install.

---

### Post by Ryadt on 2008-10-03
> **Ryadt said:**
> i686 is 32bits

i686 is 32 bits.
x86_64 is 64 bits.

---

### Post by zorkerz on 2008-10-03
So if I had installed a 64 bit ubuntu as I though I had it would report x86_64. Damn how did I pull that off. Thank you all.

---

### Post by hansdown on 2008-10-03
Here is a list of uname commands.

[http://wwwcgi.rdg.ac.uk:8081/cgi-bin/cgiwrap/wsi14/poplog/man/1/uname](http://wwwcgi.rdg.ac.uk:8081/cgi-bin/cgiwrap/wsi14/poplog/man/1/uname)

---

### Post by mindoms on 2008-10-03
This tiny c++ snippet can clearify this too.

build-essentials should be installed, though

```

#include<iostream>
int main()
{
  int size = sizeof(int) * 8;

  std::cout << "Your system is "<< size << " bit!" << std::endl;
  return size;
}

```
safe as eval_bits.cpp
In a terminal, cd to the directory where you saved that file.
```

g++ eval_bits.cpp -o eval_bits && ./eval_bits

```

Should compile and run the little prog

---

### Post by silverglade00 on 2008-10-03
Just to help out, I am running 64 bit for sure. Here is my uname -a

Linux hostname 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux

I have the x86_64 entry.

uname -m gives this information by itself.


@mindoms: I see what your code should be doing, however, it incorrectly reported me as 32 bit. Try changing to the sizeof of a long. From what I understand, int is still 32 bit.

---

### Post by LoneWolfJack on 2008-10-03
another easy way of finding out without resorting to the dreaded command line is to open firefox, click help->about and look for the text field where it will say something like

> Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.17) Gecko/20080922 Ubuntu/7.10 (gutsy) Firefox/2.0.0.17

x86_64 indicates a 64bit OS.

---

### Post by Calmatory on 2008-10-03
A bit offtopic but...

For anyone unsure about the CPU, you can use ```
cat /proc/cpuinfo
``` for information about the CPU.

---

### Post by civicwar on 2010-05-18
use the command.

uname -m

it will show:

x86_64 if that's a 64 bit version.

---

### Post by David Manas on 2011-04-28
I have Intel i7 and downloaded Ubuntu 64 bit 10.10. However, uname -a gives the architecture as i686. I suppose there is something wrong with uname, since i686 is 32 bit.  Is there any other way that I can check the architecture?  Thanks!

---

### Post by Maheriano on 2011-04-28
Download a package from somewhere like [www.frostwire.com](www.frostwire.com) and choose 64 bit. It'll tell you if it won't work.

---

