---
title: "HP laptop IDE woes"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by hugovdm on 2006-04-06
I'm having trouble with an HP nx6110 laptop. After using it for a while (can't find anything specific triggering it, except time, usually a day is enough), it "crashes" badly. I'm quite certain the "crash" is "unable to read/write hard-drive", in that I can continue playing the current mp3, next one can't be loaded though. Current programs are fine, things just go haywire (freeze) whenever the hard-drive has to be read.

Gnome/X doesn't repaint after switching to console and back. Obviously can't log-in in the console. Can't save data to disk. (I suppose I could have used a flashdisk, maybe?) I was able to get at some log files in an already-running gnome terminal (can't start a new one of course, can't close one - can't flush history to disk) and took some pictures. So for jpg's of my logs, take a look at:

[http://www.thinktoomuch.net/gallery/v/hpprob/](http://www.thinktoomuch.net/gallery/v/hpprob/)

The logs complains about hdb, oddly enough. That's why I'm now thinking it's IDE confusion rather than hard drive (hda) confusion?

We bought two laptops, helps me to admin my sister's machine as it is identical to mine. (Get something working on mine, then copy over the config.) She does not seem to have the problem though, so I believe it to be a hardware problem rather than ubuntu/software. (Maybe a workaround is possible, but that doesn't stop the fact that it is a hardware problem?)

I'm looking for confirmation that this is indeed a hardware problem, then intend to return the machine (still under warranty, 4 months old, showed the problem probably within first month already, just haven't had the time to follow-up and make the backups etc.)

Thanks in advance for any info,
Hugo van der Merwe

---

### Post by hajk on 2006-04-08
Bad hard drive, take it back for a replacement.

---

### Post by BastNic on 2006-05-03
Hey, 

I have the same laptop with sames troubles. It's very irritating. I bought this on ebay so i couldn't take it back for a remplacement. 

Any ideas ?

---

### Post by hugovdm on 2006-05-04
Eish, that sounds unfortunate. I took my laptop in, it's still in for repairs, they are waiting for a new hard drive from "overseas". Will hopefully get it back next week.

They gave me a call to ask what exactly was wrong, since they ran their tests and the hard drive seemed fine. I briefly stated the problems I was having, they replied that they will then replace the motherboard and the hard drive just to be sure! That made me really glad I bought HP, I was so expecting them to give my laptop back as it is stating "there's no problem", or maybe replacing the hard drive hoping that fixes the problem, with the problem actually being the IDE controller all along, for example.

Anyway, this is probably not good news for you. I will obviously not be able to tell you if simply replacing the hard drive was good enough.

Hugo

---

### Post by mips on 2006-05-04
Met baie eish ja ;)

What Brand HD does it use ? A lot of these laptops use Seagate drives and their 2.5" drives are probably the worst out there, their other drives are great though.

Seen a lot of failures on laptops with seagte drives, wont boot or the system crashes which causes a lovely BSOD on winxp. I also have a nx6110 with seagate drive, so far i'm lucky, touch wood, but it is probably due to the fact that I never use mine.

If you need a replacement drive just get a IBM/Hitachi Travelstar 7200rpm drive. They make the best 2.5" drives out there.

---

### Post by BastNic on 2006-05-06
Hey Mips, Do you really think that's a drive' problem ? On ubuntu I don't find what drive i have. I say you that in few minutes.

(I'm french so scuse my poor english ;))

EDIT : It's a Seagate which model is : ST9402113A. Not good isn't it ?

---

### Post by mips on 2006-05-06
[QUOTE=BastNic]Hey Mips, Do you really think that's a drive' problem ? On ubuntu I don't find what drive i have. I say you that in few minutes.

(I'm french so scuse my poor english ;))

EDIT : It's a Seagate which model is : ST9402113A. Not good isn't it ?[/QUOTE]

It could be a drive problem, the only way to be certain is to swap it out with another 2.5" drive. It could be a number of things, like HD controller or something more obscure. From personal experience and speaking to data recovery companies my conclusion is seagate 2.5" drives are shite. I have no complaints about their 3.5" drives.

So, if you can beg/borrow/steal another working drive somewhere and test it would be great.

The other shite thing is seeing that the hd's are considered part of the system/laptop and is a oem version they only have a warranty as long as the laptop. With hp it is usually a year. If you buy the drive seperately it is 3-5yrs. A nx9110 I worked on had a hd crash 1mnth outside warranty and hp would not budge or help. Just check the warranty on your laptop, it might be more than one year and then you should be able to have it replaced. You can check if it is still under warranty by using HP online interactive support (which requires IE) and speak to a person and just ask them, they will need the serial number.

Let us know how it goes.

Your english is just fine, I can speak no francais...

---

### Post by BastNic on 2006-05-07
"Le français c'est super et je fais ce que je peux en anglais"

If I well understand, I'm blocked in this situation. I just see that a 40gb 2,5" drive cost around 80-90€. On Windows, i think there are less freeze. I don't know if it's the truth but I think.

Two solutions : I wait the MacBook is out around 1000€ and i sold it for 500-600€ or i buy a drive now.

I will see..

---

### Post by mips on 2006-05-07
You could also try the diagnostics software from the seagate site or the HP diagnostics software and see if it pics anything up.

---

### Post by BastNic on 2006-05-07
I juste tried it. I went on seagate' website, download the desktop analyser, burn it. I tried all tests : no problem, no error.

It's wired, but I would prefered that it's a hd's problem. In this case, i should repare it and it wiil be good. "Tant pis"...

If you have another idea ;)

---

### Post by mips on 2006-05-07
[QUOTE=BastNic]
If you have another idea ;)[/QUOTE]

Nope, i've run out of ideas at this point...

---

### Post by BastNic on 2006-05-07
It sucks... (I don't know if i can say that on an english forum, correct me if it's not correct).

I don't understand. I will be angry :(.

---

### Post by mips on 2006-05-07
[QUOTE=BastNic]It sucks... (I don't know if i can say that on an english forum, correct me if it's not correct).

I don't understand. I will be angry :(.[/QUOTE]

It's ok to say 'sucks'.

---

### Post by mips on 2006-05-07
I just looked at Hugo's screenshots of the logs.

HDB refers to the CD Rom drive. I also google the error in the log and found quite a few references to it. There is even a bug on Ubuntu Launchpad. [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/15221](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/15221)

Some people seem to experience crashes, others just have problems burning CD.

Something to try:
Download the latest Dapper Beta2 daily build CD from here **[COLOR="Red"]http://cdimages.ubuntu.com/daily/current/[/COLOR]**
Burn the image to cd.
Backup your data.
Delete existing ubuntu partion.
Do a fresh dapper install.

---

### Post by BastNic on 2006-05-09
I'm back..

I'm on last Dapper release. But for one of my works I've to be on Windows. I developpe on "WebDev" (a PCSoft'soft) for clients. It's only on Win and sometimes he crashes too ! Everything block, at this moment it's impossible to write anything on the drive. It finishes with a very pretty BLue Screen. (I don't know how we say that in English).

So I think this is really an hard drive's problem. When my project on WebDev will be finished I will do a fresh install. Certainly I also format my drive completly more than once.

---

### Post by hugovdm on 2006-05-10
I had no problems with recording a number of CDs with cdrecord. I did notice the error message looked like it refers to the CD, so I'm concerned that when I get my laptop back, with new motherboard and hard drive, that the problem still persists. Then I'll know to replace the CD drive next. Argh. (Well, I'll also first try Dapper and see if that helps.)

Note that my sister has an identical laptop that does not have this problem.

Hugo

---

### Post by BastNic on 2006-05-10
You're right hugo.

My grand Brother has the same. He's only on Windows and I never heard that he has any troubles. I can switch it 'ni vu ni connu'.

Indeed no, I can't ;) 

So hugo, you think this is a CD drive 's problems ? If it's just that, i will deconnect it : I never use it.

---

### Post by hugovdm on 2006-05-10
I don't know, I hope not ;), but maybe it's worth a try to disconnect it. If that works for you, let me know. I don't know when I'm getting my laptop back, I'm still hoping this week...

---

### Post by BastNic on 2006-05-10
I don't know if it's an hallucination but i think i have'nt any freeze since yesterday. It's wired !

Before try anything, i wait another freeze ;).

---

### Post by Greg2 on 2006-05-10
[QUOTE=BastNic]
you think this is a CD drive 's problems ? If it's just that, i will deconnect it : I never use it.[/QUOTE]
You could try to pass the following parameters to the kernel by editing the kernel boot line in /boot/grub/menu.1st with```
hdc=noprobe hdc=cdrom
```If you still have a problem, could you post your dmesg output shortly after a clean boot?

---

### Post by BastNic on 2006-05-10
I confirm that I just dreamed.

Greg : I add it, I reboot and I let you know ;). I hope that will correct your problems ! Thanks.

EDIT : He has many problems to boot just with that... i just keep the hdc=noprobe for test.

EDIT2 : I'm back..... After an enormous freeze ! So.... conclude yourself. I feel bad :(

---

