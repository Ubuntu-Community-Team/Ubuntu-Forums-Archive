---
title: "Ubuntu server only showing 3% of ram with free -m"
date: 2016-09-15
forum: Hardware
---

### Post by liste on 2016-09-15
I recently tried to install Ubuntu server 16.04 64-bit on my Dell Poweredge SC 1425, but got the error "Load installer components from cd", so after trying multiple work-arounds, I finally decided to install Ubuntu server 64-bit on my AMD 64-bit PC and then transfer the hard drive.  The server is now up and running fine on the Poweredge, except for one thing: the ram.

[free -m] says that my total memory is 235 MB.
[htop] reveals 236 MB. 

 However I have 8GB installed on the machine and I know that all 8GB are functional because I was trying out Ubuntu 16.04 desktop 64-bit on the machine, and all 8GB were recognized.

[sudo lshw -class memory] shows that my first 4 banks do indeed each have 2GB of DDR2 Synchronous 400 Mhz (2.5ms) sticks of memory installed.

As a side-note: loooking for a solution on the web is showing up a lot of posts about 32-bit vs 64-bit problems, but that is obviously not my issue.  I also found someone who was complaining about lacking ~150MB out of 6GB of ram, so that doesn't really fit my problem either.  It seems unlikely that a BIOS update should be required seeing as Ubuntu desktop 16 found all the ram.

What can I do to get all of my RAM functional?  Having only 3% available obviously isn't very efficient on my server.

Thank you.

---

### Post by Bucky Ball on 2016-09-15
Don't see how it's obvious. You haven't stated definitively or confirmed that you aren't using the 32bit version. Presume you've double-checked. ;)

The 32bit version won't see that much RAM, but you probably know that ...

---

### Post by liste on 2016-09-15
Oops, sorry!  You're right: I forgot to specify that I was installing Ubutntu server 64-bit.  Yes, I have double-checked that, and it is 64-bit.  I have updated my original post to reflect that.

[uname -m] output is x86_64.

Also, if it were a 32-bit issue, I would expect to see more than just 236 MB of available RAM.  Somewhere around 3GB would be more logical.

---

### Post by Bucky Ball on 2016-09-16
> **liste said:**
> Also, if it were a 32-bit issue, I would expect to see more than just 236 MB of available RAM.  Somewhere around 3GB would be more logical.

True, but ya just never know ... odd things happen round here! :)

Bit of a mystery. Obviously something weird going on with the server version but beats me what.

---

### Post by SeijiSensei on 2016-09-16
What if you boot from an installation disc and choose "Try Ubuntu?" How much memory is reported then?

---

### Post by liste on 2016-09-16
Ah, I have found the problem.  My brother was trying to install Hackintosh on the machine and turned on the OS Install Mode in the BIOS.

Here's where I found the answer: [http://en.community.dell.com/support-forums/servers/f/956/t/3940745](http://en.community.dell.com/support-forums/servers/f/956/t/3940745)

Thank you for your help!

---

