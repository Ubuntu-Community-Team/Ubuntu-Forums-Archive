---
title: "Ubuntu install hangs at 27% on Dell XPS M1330"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by sreeramkumars on 2009-04-04
Hi,

I am a Ubuntu newbie and trying to install 8.10 on my dell xps M1330 laptop.
The laptop has dell media direct, Vista installed on a 7200rpm 320GB harddisk and 4GB memory. 
I downloaded ubuntu installer for 32 bit and burnt the cd. Booting the CD is no problem, I get onto Ubuntu. Clicking on instal takes me to the 7 steps required for the installation. I chose manual partition option and allocated 50GB for ext3 / and 6GB for swap. There is about 135GB unallocated freespace still left. Vista has taken up the other 100GB.

All the 7 steps go through fine..but when the actual installation starts, it hangs at about 27% at step installing system- copying files.
CD itself seems fine, as ubuntu gets invoked, wireless works, firefox works and in fact I am sending this msg from ubuntu firefox loaded by CD.

Any help is much appreciated as I am desperate to get Ubunto going..

PS: retried the whole process from scratch about 3 times and same result :(

Regards
-Sreeram.

---

### Post by b@sh_n3rd on 2009-04-04
Did you burn the LiveCD on a CD-RW? And at what speed did u burn it? Linux distro's are are highly compressed and you are required to burn the CD images at the lowest possible speed to avoid any errors.

---

### Post by asuastrophysics on 2009-04-04
since it's digital, i dont think quality is affected by burn speed.

however,

does the cd have any scratches on it? i've had installation stop numerous times because of a scratched up disk

---

### Post by sreeramkumars on 2009-04-04
Hi,

Tried 3 DVD-Rs so far with various speeds from 8X-2X.

The problem persists. :-(

---

### Post by b@sh_n3rd on 2009-04-04
Did you burn the DVD's on the same laptop and if so, boot with 'em, on the same system, immediately after that? Did you attempt the installation with a cold boot? When the machine gets hot, it may cause read errors. And, a computer tends to freeze. Just give it a try.

---

### Post by b@sh_n3rd on 2009-04-04
Did you burn the DVD's on the same laptop and if so, boot with 'em, on the same system, immediately after that? Did you attempt the installation with a cold boot? When the machine gets hot, it may cause read errors. And, a computer tends to freeze. Just give it a try. :)

---

### Post by tlois on 2009-04-04
Have you given it enough time to go through the process?  Is it possible that it is installing, but just looks at though it is hanging on that percentage?  I just posted about an install that looked as though it was hanging at 0%, but was actually working.  If you haven't already, can you walk away from it for 30 mins or so and see if maybe that is what is happening?

---

### Post by b@sh_n3rd on 2009-04-04
Good idea, I thought of that too but didn't really register in my brain to say it :D

---

### Post by tlois on 2009-04-04
The only reason I have all that on the brain is because I have gone a little Ubuntu-install crazy and have been pulling out every old laptop and cpu within 10 miles to put it on, so have lately run into about every install issue possible!  

I have even gotten my dad to let me do an install on both his laptop and CPU- only as dual boot with Windows for now, but I have faith that once he sees he no longer has to do all that high maintenance Windows stuff, he will see the light too.

---

### Post by sreeramkumars on 2009-04-04
Hi,

1) I tried 2 DVDs and 2 CDRs from different PCs at 2X,4X,8X. Same result for all the 3.

2) I left the system run for a couple of hours..(praying each minute during that time) :-( but same result.

Regards,
-Sreeram.

---

### Post by tlois on 2009-04-04
OK, someone will hopefully come along with a better solution.

Another idea though:  have you tried installing via usb flash drive with Unetbootin?

---

### Post by b@sh_n3rd on 2009-04-04
That kind of "freezing" problem comes up on one of my comps when it overheats. Even the video goes haywire. Except for that, i can't think of any other reason but i'll try to think of one.

[QUOTE]I have even gotten my dad to let me do an install on both his laptop and CPU- only as dual boot with Windows for now, but I have faith that once he sees he no longer has to do all that high maintenance Windows stuff, he will see the light too./QUOTE]

:D HEY tlois, same here. My dad's just scared that he might not be able to mess around with MS-WORD and EXCEL despite my reassurances. But he quite likes Ubuntu and once he too asked me to dual-boot his PC :D. Furthermore, i've bored all my friends and sisters to death with the word "Ubuntu" :D Who can blame me huh? Ubuntu's just too good and too cool! haha. Unfortunately they don't see it. :( What a sad world we live in...:D LOL!

---

### Post by sreeramkumars on 2009-04-05
Update:

Thought I would give 8.0.4 LTS a try and it worked like a charm. No issues whatsoever. So it seems to be an issue with the 8.1.0 installer.

Am finally now on Ubuntu :guitar: and installing all the required drivers/software:popcorn:

Its fun once you are onto Ubuntu. ):P to windows.

Thanks for all those who tried to resolve my problem.

Regards,
-Sreeram.

---

### Post by b@sh_n3rd on 2009-04-05
Hey, cool, congrats! Have fun with Ubuntu! And welcome to the community! :D

---

### Post by sreeramkumars on 2009-04-06
Thanks.

After installing 8.0.4, I upgraded to 8.1.0 and its all fine.

A bit of roundabout way and frustated moments to reach here...but its all worth it considering the ubuntu experience. Kept me awake till early morning...:p

---

