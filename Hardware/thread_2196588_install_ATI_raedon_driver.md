---
title: "install ATI raedon driver"
date: 2013-12-30
forum: Hardware
---

### Post by selmanii300 on 2013-12-30
hi to every one how are reading this post i v installed ubuntu on my laptop but i m not satisfied with ubuntu default resolution and i would like to install my graphic driver all i know that she is a  ATI can you please help me how to do beacause i m a beginer with ubuntu thank's to all

---

### Post by Mark Phelps on 2013-12-30
> all i know that she is a ATI 

Sorry ... but that is not nearly enough info for anyone to provide detailed advice.

We need to know the make and model AMD video chipset you're using.

To find out, open a terminal, enter "lspci" (without the quotes), look for the line containing "VGA" -- and post that line back here for us to see.

After that, we can provide you some details.

Also ... need to know WHICH version of Ubuntu you are running.

---

### Post by selmanii300 on 2013-12-30
oki Mark that's the return of the commande i hope that i m right 
> anis@anis-HP-Compaq-6830s:~$ lspci | grep "VGA"
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 95c2

 
and i m using a ubuntu 12.04 lts sorry i forget to mention that

---

### Post by QIII on 2013-12-30
If I am not mistaken, the 95c2 is an HD 3000 Mobility series GPU.

The last version of Ubuntu for which ATI has a supported driver is 12.04.1.  If you are using 12.04.2 or later, you will not be able to use an ATI proprietary driver with that GPU.  There is not much that can be done about this, since the proprietary drivers are closed source.

Are you using 12.04.2?

---

### Post by selmanii300 on 2013-12-30
:cry: :frown: reading your reply mr[**[COLOR=#C61919][B] QIII**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=628170") did not encourage me to use ubuntu

---

### Post by mörgæs on 2013-12-30
Take your disappointment to AMD/ATI. It's their decision not to support their cards.

---

### Post by QIII on 2013-12-30
Not just Ubuntu.  Any Linux distribution that uses the current X Server will face the same problem.  ATI has put the driver for that GPU in a legacy branch and is not updating it.  Any dissatisfaction with the situation should be directed at ATI, not Linux.

You could go back to 12.04 or 12.04.1, each of which will be supported until April, 2017.

---

### Post by deadflowr on 2013-12-30
> [COLOR=#000000]You could go back to 12.04 or 12.04.1, each of which will be supported until April, 2017.[/COLOR]

Aye, you can find those here
[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)

There is a dropdown list below the top section that lists the archive iso's.
Look for the one marked either
[COLOR=#000000]ubuntu-12.04-desktop-amd64.iso (for 64-bit)
[/COLOR][COLOR=#000000]or
[/COLOR][COLOR=#000000]ubuntu-12.04-desktop-i386.iso (for 32-bit)
They will have an April 25 2012 date.

If you install either, You will get and keep the original precise kernel and X stack, it will be fully supported through the support length of the precise release.
More
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Added: Whether or not it helps solve the resolution problem would probably be a different thing though.[/COLOR]

---

