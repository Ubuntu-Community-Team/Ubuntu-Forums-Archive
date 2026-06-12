---
title: "4GB in 32bit -&gt; random crash"
date: 2009-03-25
forum: Hardware
---

### Post by TwiStEr55 on 2009-03-25
This is not the typical question .. why dont I have the full 4GB!

I knew I would only have 3Gb+ in intrepid 32bit.


The memory is set up correctly and Memtest86 2.11 is clean .. no errors!

Everything boots up normal .. my system randomly crashes in the form of a complete freeze. I was playing VLC at the times, but that might be just a coincidence I have the RAM just since today.

I had a game crash in Windows XP 32bit as well .. I still think it is in the software, why else would memtest return no errors?

greets Matt

---

### Post by Dougie187 on 2009-03-25
AFAIK You can only use 4gigs of ram in 64 bit.

32 bit only allows for 3.2 gigs or less

---

### Post by TwiStEr55 on 2009-03-25
i do know that .... but i should be able to operate my system with the 3.2GB available right? ... i dont car that the last 0.8GB are not available ... but at the moment I get these crashes ... anybody experience this?

---

### Post by Dougie187 on 2009-03-25
Did you try checking any of your logs?
In a terminal you can type any of the following commands to view logs.

```

dmesg
less /var/log/syslog
less /var/log/messages 
```

There is also a system log viewer in System->Administration

---

### Post by shatterblast on 2009-03-25
You really do need a 64-bit operating system if you want 4 Gb of memory.  Windows XP Professional can handle it natively I believe, and it costs roughly $40 now in US dollars, though you could probably get it cheaper some other way.  Windows XP SP2 can possibly read 4 Gb of RAM fine if you add "/3GB" somewhere in the boot.ini file.  It apparently will slow down at least a little, and a hardware conflict could cause a problem.  The 64-bit thing is really a software limitation in my view.

I think I've seen a couple of 64-bit operating systems for servers go 8 Gb, 16 Gb, and ridiculously higher, but I think it requires some custom software I'm unfamiliar with.  Even if the option easily exists, it would still be best performance-wise to just go straight to 64-bit for gaming reasons.  I'm not sure if an option presently exists to convert from 32-bit to 64-bit Ubuntu, though I know it possible to do without losing much.

Also if deciding to convert from XP to XP Pro, please use caution and back-up your data.

---

### Post by impact on 2009-03-25
> **TwiStEr55 said:**
> This is not the typical question .. why dont I have the full 4GB!

I knew I would only have 3Gb+ in intrepid 32bit.


The memory is set up correctly and Memtest86 2.11 is clean .. no errors!

Everything boots up normal .. my system randomly crashes in the form of a complete freeze. I was playing VLC at the times, but that might be just a coincidence I have the RAM just since today.

I had a game crash in Windows XP 32bit as well .. I still think it is in the software, why else would memtest return no errors?

greets Matt

I did experience similar crashes but it was probably because of an older version of nvidia drivers, I found some strange error messages in Xorg.log. Definitely check all logs for any messages.

Also, let memtest run longer.

---

### Post by TwiStEr55 on 2009-03-25
I know of the software limitation with RAM ... but I was under the impression that I would still be able to operate a stable system with the max supported RAM which is the 3.2GB .... is this correct?

---

### Post by shatterblast on 2009-03-25
Memtest is separate from operating systems themselves.  While that particular software has its ability to test memory's reliability, this feature becomes independent of whatever else lets your programs run.  The "other" software, like Windows and Ubuntu, have dependencies in different forms that allow your computer to just work properly.  These dependencies can prove quite picky about their environments.

---

### Post by TwiStEr55 on 2009-03-25
I just havnt read anything like this... everything I found was just people complaining of not having the total 4GB. 

I as well think its something in the software itself since memtest comes through clean ... so the memory itself is not to blame .... I have a spare hard drive on which ill install intrepid amd64 tomorrow and if the issue does not persist all is good and ill switch to the new RAM completly when jaunty is released ... ill test XP 64bit as well and see if it wont freeze either ...

---

### Post by shatterblast on 2009-03-26
To further complicate things, hardware drivers, firmware, and software libraries each add to an issue of "stability."  It's a concept that includes any operating system really.  Installing or updating a graphics driver affects just about any operating system for example, especially when trying to get Direct X or OpenGL to work.

The issue could even extend to the main board in some way.  How ever, the computer could still remain perfectly fine.  It might just exist as a hardware conflict, which operating systems resolve.  I took this as a guess since Windows came up in the topic.  Most graphics-intensive software in my opinion lean toward the nastier side when compatibility enters as a question, though the fixes can arise both as easy and time-consuming.

---

### Post by TwiStEr55 on 2009-03-26
ok .. so i hooked up the old drive and installed xp64bit and intrepid 64bit .... i actived memory remapping in the bios and as a result I had the entrie 4GB in ubuntu and windows .... but in both systems i got sudden reboots .... i deactived memory remapping and tested for half an hour till now and no crashes but only with 3.2 GB ....

i wont mind If im only able to run 3.2GB, but does anybody hav an answer why I get these random reboots?

memtest is clean .... it must be the memory since if I switch to my old 2GB everything is fine ... but the new memory checks out completly fine in memtest .. i dont get it ....

---

