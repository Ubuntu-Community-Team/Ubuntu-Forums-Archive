---
title: "Ubuntu kernel error on Acer Swift 3 laptop"
date: 2017-07-17
forum: Hardware
---

### Post by danriel on 2017-07-17
Hello all

I bought last year a cheap but beautiful laptop in order to install Linux on it. Little did I know that Acer is not renowned for their Linux support.

I tried installing quite many different distros on the Acer Swift 3, the only one that works is Ubuntu in its flavour Xubuntu 32 bits. And it works fine most of the time.

My problem is that when starting the computer, there is a 50% chance to end up in a kernel panic.

I got used to it in time. Restarting in recovery mode usually works then I restart again and it works fine. 

I wonder whether there wouldn't be a solution to this problem.

Here is a print screen of the kernel panic.

[IMG]http://destresser.fr/fichiers/printscreen.jpg[/IMG]
[http://destresser.fr/fichiers/printscreen.jpg ]("http://destresser.fr/fichiers/printscreen.jpg")

What are your suggestions ? What should I do or try ? 

Thanks for any help ?

Long live Linux ! :)

---

### Post by BenginM on 2017-07-17
Salutations! and welcome to the forums.


also, we might need to see the logs , so in a terminal run:

sudo lsb_release -a ; uname -a

and paste the output in a ```
 tag like the following example:

[CODE]
sm@tru:~$ sudo lsb_release -a ; uname -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial
Linux tru 4.11.0-8.2-liquorix-amd64 #1 ZEN SMP PREEMPT liquorix 4.11-16 (2017-07-04) x86_64 x86_64 x86_64 GNU/Linux

```

also, run:

sudo cat /var/log/kern.log | curl -F 'sprunge=<-' [http://sprunge.us](http://sprunge.us)

and paste the new link , thanks.

---

### Post by Bashing-om on 2017-07-17
danriel; Hello too :)

Are we looking at vendor lock-in ?
See:
[https://sites.google.com/site/easylinuxtipsproject/windows#TOC-Change-some-UEFI-settings](https://sites.google.com/site/easylinuxtipsproject/windows#TOC-Change-some-UEFI-settings) <- Windows 8.x and 10: how to prepare it for dual boot with Ubuntu 
see: [http://ubuntuforums.org/showthread.php?t=2330267](http://ubuntuforums.org/showthread.php?t=2330267) <-  set "trust" on the Ubuntu/grub .efi files.
[https://ubuntuforums.org/showthread.php?t=2333630](https://ubuntuforums.org/showthread.php?t=2333630) <- oldfred : Ubuntu on Acer Aspire new Laptop 
[https://ubuntuforums.org/showthread.php?t=2332385#post13525158](https://ubuntuforums.org/showthread.php?t=2332385#post13525158) <- Re: Installing Linux on A Acer desktop

[INDENT][INDENT]trials, troubles and tribulations
[INDENT][INDENT][INDENT]but many have overcome
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by saeliux on 2017-12-02
I don't want to keep windows 10 on my acer swift 3. I am now thinking of returning it. Did this ever get resolved?

---

### Post by mörgæs on 2017-12-04
One way of finding out is to test Ubuntu in a live boot. Have you tried that?

---

