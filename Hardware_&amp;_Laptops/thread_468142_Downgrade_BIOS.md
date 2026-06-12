---
title: "Downgrade BIOS"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by cdevilrun on 2007-06-08
Hi!

I have a Dell Inspiron 600m. Apparently the A07 BIOS upgrade for the Phoenix motherboards that these use instituted an "optimization". When the box reaches 70C the processor speed drops to 600Mhz. This is causing some interesting lag issues with games.

The Question:

All I have is the EXE file to flash the BIOS with. It won't work in wine. How do I downgrade the BIOS?

Thank you for your assistance.

---

### Post by Megatog615 on 2007-06-08
Best way to do it would be through a DOS bootdisk.

---

### Post by cdevilrun on 2007-06-08
Yeah, that's what I figured.

Would you mind giving me a short step-by-step?

I'm not new to computers or Linux, this just isn't something I've dealt with. At least with Linux I'm self-taught.

So, instructions...

Tell me what DOS version I should get a boot disk for.
How do I add the exe to the CD in a way that I'll be able to access it when I boot.

Thanks!

---

### Post by CrispyFried on 2007-06-08
[www.bootdisk.com](www.bootdisk.com) has tons of bootdisk images. do you have a floppy?

---

### Post by cdevilrun on 2007-06-08
No, just a CD. But the BIOS now allows for booting from CD.

And I've been to the website which is why I asked which image I needed.

---

### Post by CrispyFried on 2007-06-08
ok this is the way I remember doing it, although I used drdos instead of dos 6.22, but they should be the same.

you need a cd burner program that will allow you to make bootable cdroms, most cd writer proggies allow this. grab the dos 6.22 disk file from bootdisk.com. all you want from the zip is the 622c.img file, ignore the rest.

fire up the cd writer proggie and tell it you want to make a bootable cdrom. when it asks for the boot disk image, point it at the 622c.img file. it will read it. then put the exe used for flashing your bios into the normal data area of cd writer program. burn it and boot it. it should boot to dos 6.22 with the cdrom drivers loaded and be sitting at the a:\ prompt. it will have told you the drive letter of the cd during the boot (look for the message as it boots, it may scroll off the screen) so just switch to it and execute the .exe file.

WARNING: please be aware that updating your bios is not a trivial thing to do, its easy to make a brick out of your notebook if it fails. Ive tried to make sure my steps are OK but still make sure to read all prompts that pop up when doing this, if any warnings, especially about the bios being the wrong version, are given stop. your flash exe should promt you to save a copy of your existing bios but you wont be able to do so. if youre unsure of any of these steps please dont try this.

edit: also if youre downgrading you may lose the option of booting from cdrom (unlikely but possible) so be absolutely sure you want to do this. it may be a one way ticket.

---

### Post by cdevilrun on 2007-06-09
Ok, so here's my next question.

622C.IMG is not an ISO. So nothing I have recognizes it as such.

I tried renaming the file extension but the native burning program (through right-clicking) says it's not a valid ISO.

GnomeBaker doesn't give me an option to add other files before burning the file as an ISO.

Is there a program and method you recommend for burning the two files to CD?

---

### Post by cdevilrun on 2007-06-09
Ok, I managed to find a program to burn this IMG as an ISO

Of course, it only allows me ~1.4MB as a bootdisk.

Can I burn the BIOS flasher seperately? Do I need to delete utilities from the 622C file to make room?

I need 600KB +

---

### Post by ramjet_1953 on 2007-06-09
Before going ahead, there are a few issues to consider here:

1. The reason why the processor throttles down at 70 C is very good. If you continue to operate at this temperature, or above, you will cook your CPU. That is exactly why it throttles back.

2. Re-flashing a BIOS is a risky business at the best of times. Unluss you have a dual BIOS system, if something goes wrong, you will end up with a dead motherboard.

3. The answer is better cooling for your system, not defeating a safety feature.

Regards,
Roger :cool:

---

### Post by CrispyFried on 2007-06-10
> **cdevilrun said:**
> Ok, I managed to find a program to burn this IMG as an ISO

Of course, it only allows me ~1.4MB as a bootdisk.
Can I burn the BIOS flasher seperately? Do I need to delete utilities from the 622C file to make room?


you dont need to delete any files from the img, when you make a bootable CD you can still burn 600+ mb to the normal cd data area and it will be readable (as a normal cd with its own drive letter, with the boot img as a:) after the boot.. the boot image just takes up a small part of the CD, the rest of it is a treated as a regular data cd. somewwhere in your cd burner program you should be able to make it bootable, point it at the 6.22 img and still have 600+ megs left to put your flasher in. Ive never seen a cd burner program that doesnt allow you to add to the normal data are of a bootable cd. 

as for deleting stuff from the img if you can find a way to edit the img (I never have tried) I think the 6.22 disk creates a ram disk using a cab file and loads everything to it.. pretty sure the cd drivers are in the cab files so you cant delete it.

I cant remember if you can swap cds after booting from one, but you could try burning the flasher to another one and give it a shot. personally with something as risky as a bios flash I wouldnt try.

does the cd boot to an a:\ prompt? if it does you should be able to see the cd as drive c: d: or e: , depending. it should be empty or just show the flash exe, depending on how far you get. 

> **ramjet_1953 said:**
> Before going ahead, there are a few issues to consider here:

1. The reason why the processor throttles down at 70 C is very good. If you continue to operate at this temperature, or above, you will cook your CPU. That is exactly why it throttles back.

2. Re-flashing a BIOS is a risky business at the best of times. Unluss you have a dual BIOS system, if something goes wrong, you will end up with a dead motherboard.

3. The answer is better cooling for your system, not defeating a safety feature.


I agree 100% sure would suck major pond water if you did the flash and cooked your cpu.

---

### Post by cdevilrun on 2007-06-10
Hmm, like before I can't write the IMG file as a bootable CD. 
Any linux program I have only writes ISO files as images.

Do you have a specific program in mind?

Regarding downgrading the BIOS. Hey, it worked well enough for BIOS versions A01-A06 right? ;-)
On a serious note, this method has been talked about a lot in several different sources I've found. It's a problem many people are having. And downgrading the BIOS seems to work.

---

### Post by CrispyFried on 2007-06-10
ok, I just made a bootable cd using k3b in Ubuntu (never made one in Ubuntu before) and it worked.

the files at bootdisk.com seem to have changed (was zips, now its exes?), so if your filename doesnt match go back and grab the 6.22 disk image again. it was named boot622.exe. open using archive manager and extract the boot622.ima (yes, .is**A**, not im**G** this time but Im pretty sure theyre the same thing, just different names so you should be able to use the 622c.img file too) file to your desktop or wherever. I got an error message about it not liking the .exe file but the boot622.ima file extracted fine.

fire up k3b (it parks itself under applications -> sound and video) and select "new data cd." when it opens the interface goto the "Projects -> edit boot images" menu. from there click "new" and browse to whatever folder you put the boot622.ima file and select it. I get a huge error window stating that no *.img files are found, click "cancel" if you do too, then click "new" again and it will list the files in the folder this time. select boot622.ima and click ok. youll go back to the cd layout window and a "boot" directory will be there. now find your flasher proggie and add it to the layout window (**under** the boot dir, not in it) too. 

now to burn, so click "burn."  when the burn window came up I selected "dos compatible" for the filesystem. maybe its not needed but I did it anyway. then burn it and boot it. mine came right up to an A:\ prompt and told me the cd was drive "R:" so I went to R: and lo, my test file was there.

have fun. but please be careful with that flash. I have a UPS and I still cringe whenever I flash my BIOSes.

---

### Post by cdevilrun on 2007-06-13
After all that, the A06 BIOS doesn't support the hardware.

Ah well, c'est la vie.

Thank you for your help and tutelage. I came away with a better cd-burning program and knowledge of making a bootdisk for Ubuntu.

---

