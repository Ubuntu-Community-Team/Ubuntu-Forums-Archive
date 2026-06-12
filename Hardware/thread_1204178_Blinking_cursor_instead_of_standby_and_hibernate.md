---
title: "Blinking cursor instead of standby and hibernate"
date: 2009-07-04
forum: Hardware
---

### Post by Sukhinov on 2009-07-04
Subj.

P.S. 3 years ago I tried to set Mandrake on my Acer TravelMate 330. The standby and hibernate were not working there. Now I am trying to set Ubuntu on Asus R2E. Standby and hibernate still not working. The system is useless without these functions. How many years I should wait till Linux will work out-of-the-box (like Windows)?

---

### Post by Sukhinov on 2009-07-05
Here is automatically generated report by Apport:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/395570](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/395570)

---

### Post by Sukhinov on 2009-07-05
Here is logs I done when trying to Standby (according to these instructions [https://wiki.ubuntu.com/DebuggingGNOMEPowerManager](https://wiki.ubuntu.com/DebuggingGNOMEPowerManager))

---

### Post by richardgundersen on 2009-07-06
Hi I have exactly the same problem, not sure where to start - did you get anywhere with it?

This thread looked promising: [http://ubuntuforums.org/showthread.php?t=300600](http://ubuntuforums.org/showthread.php?t=300600)

But when I got to this line, 

    sudo nano -w /etc/initramfs-tools/conf.d/resume

...it says change the device name. But there's no device name in there, just some UUID thing. 

One of the replies on that thread also mentions an encrypted swap partition. Could anyone tell me how to check if mine is encrypted, in case that's the problem?

Please help, it would be FANTASTIC to have working Hibernate functionality.

---

### Post by poncedeleon on 2009-07-11
I'm having the same problem here.
Tried all suggestions I could find([https://bugs.launchpad.net/ubuntu/+bug/378670](https://bugs.launchpad.net/ubuntu/+bug/378670) , [http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/](http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/), [https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume)) but none of them worked to me. I also tried to debug hibernate but  could not make it work.

Any suggestions ?


Thanks

---

### Post by poncedeleon on 2009-07-28
I just installed [tuxonice]("http://www.tuxonice.net/") and  hibernate now works perfectly.

---

### Post by darco on 2009-07-28
> **poncedeleon said:**
> I just installed [tuxonice]("http://www.tuxonice.net/") and  hibernate now works perfectly.
uggh..you have to compile your kernel to get that to work? Ill pass

darco

---

### Post by poncedeleon on 2009-07-29
darco,
[COLOR=Black]
There is no need to recompile the kernel. 
You can[/COLOR] get a version of tuxonice from ubuntu repositories. The package[COLOR=Black] name is **tuxonice-userui**[/COLOR]. Try installing it.
After installing it you can test the hibernate function with the command **sudo /usr/sbin/hibernate** .


Good Luck

---

