---
title: "ACPI : Aborted because bad gzip magic numbers"
date: 2008-11-16
forum: General Help
---

### Post by hungerkuenstler23 on 2008-11-16
Hi all

First of all sorry for my bad english.

I have a strange problem:

I have recently installed ubuntu like this:

I have 4 Sata2 HD's and 1 IDE HD.

On the IDE i have Windows XP.

On one Sata2 i have the new Ubuntu version.

Everything worked fine until yesterday.

I think i installed Zattoo and a "sensor detector tool" before shoting down the day before.
The next day i tried to Boot but o got this error:

Boot from [hd0,0] ext3
Starting up
[0,269945]ACPI : Aborted because bad gzip magic numbers
[0,280017]..MP-Bios bug: 8254 timer not connected to IO-APIC
[0,433845]Kernel Panic - not syning : VFS : Unable to mount root fs on unknown-block (0,0)

The only thing i can do is reboot and boot from the windows HD

I havent found anything on this or other forums. 

please help me guys

greetings from switzerland

---

### Post by dcstar on 2008-11-17
> **hungerkuenstler23 said:**
> 
.......
Boot from [hd0,0] ext3
Starting up
[0,269945]ACPI : Aborted because bad gzip magic numbers
[0,280017]..MP-Bios bug: 8254 timer not connected to IO-APIC
[0,433845]Kernel Panic - not syning : VFS : Unable to mount root fs on unknown-block (0,0)
......

Looks like some boot files have been corrupted, I don't really know how to fix this apart from re-installing.

---

### Post by MaddMatt on 2009-01-22
Hi, 

I know this was a while ago, but I figured out how to do this; a re-installation is not necessary - you just need to replace your initramfs. 

Simply boot into a different kernel, or a rescue disk. From the rescue prompt, run this command (as root):

```
update-initramfs -k all -c -v
```

Probably too late, but hope this helps for future reference. \

Cheers,
m

---

### Post by trickyhu on 2009-04-16
Thanks for posting the solution MaddMatt! I just ran into the problem and it fixed it for me.

---

### Post by Merlin_ua on 2009-04-26
> **MaddMatt said:**
> Hi, 

Simply boot into a different kernel, or a rescue disk. From the rescue prompt, run this command (as root):

```
update-initramfs -k all -c -v
```



Hello!

I have exactly the same problem with a newly installed 9.04. Can anyone please advice how do I boot into a rescue mode? When I just boot from the LiveCD the command mentioned above complains that it is booted from a read-only media.

I don't have any "rescue" option in my CD (ordinary desktop Ubuntu CD).

When I try the "recovery mode" from the GRUB menu I receive exactly the same kernel panic and can't do anything...

Thanks in advance!

---

### Post by sekura on 2009-05-15
I too would like to know how to run the command from the Live Session, as i have it on an USB stick, and it automatically starts.

Same thing happened to me:
-I have 2 HDs. On one, i have XP, on the other, i have very recently installed Ubuntu 9,04 (my first ubuntu ever, so note that i am a beginner). Boot loader is installed on the ubuntu HD (hd1).
-Installed all the critical and recomended updates it could offer me (aprox 40mb)
-Enabled ATI driver + restart
-Made a visual tour (no touching, at least thats what i think) trough most of the System -> Prefferences.
-weeeird crashy artifacts when played with the screensavers.(Pidgin was running too) some windows became invisible, and i wasnt knowing what i was dragging on. Finally managed to click the restart button on the INVISIBLE dropdown menu
-got the same errors except for the MP-Bios bug.

I finaly resolved with a clean install, but am expecting another fail. 

Information would be great.

---

### Post by retromodcoza on 2009-08-25
I took the hard drive loaded with ubuntu out of one computer and into another as the main drive. I received this error message.

I typed in Maddmatts line - and it fixed the problem. Thanks.

Can you give a little insight into what I just did?

Thanks
Lloyd

---

### Post by ffg1977 on 2009-10-16
It worked for me too. Thanks, MaddMatt.
Don't forget to run it as root ("sudo update-initramfs ...").
Regards.

---

### Post by akavinski on 2009-10-19
I just transfered all work I had from win to Ubuntu, pointing mid-finger to all win guys but as a noob encountered to me enormus problem...
It seems that ubuntu auto-updated software and after that when I tried to boot system I got this message :

[0,269945]ACPI : Aborted because bad gzip magic numbers
[0,433845]Kernel Panic - not syning : VFS : Unable to mount root fs on unknown-block (0,0)

I tried to boot in rescue mode - that failed too.
I looked through forum but could not find solution.
And I dont have any previous kernel images to boot on.

Can anyone help me please ?
I need help urdent.

---

### Post by laceration on 2009-10-19
akavinski, it says above
> or a rescue disk
Do you still have the CD you installed Ubuntu from?  That will work.  You might have to go into the bios to make it boot from the disk drive.

---

### Post by akavinski on 2009-10-19
Yes, I've changed boot line to  rescue, when I boot from installation CD - but it STILL dumps message that it can't be booted.
I really didn't do anything odd to system and if someone can explain me why it happened I'll be glad just to know.

thanx for reply !

---

### Post by ffg1977 on 2009-10-20
akavinski, it worked for me when I changed kernel version from 2.6.28-15 to 2.6.28-11. Rescue mode didn't work too. This option appears in grub menu. Hope it works.
Regards.

---

### Post by akavinski on 2009-10-20
Thank you ffg1977, I tried everything but no luck. Now I reinstalled system and it works again...but...I really really want to know WHY this happened I can't go on working on Ubuntu if this kind of problems occure sometimes unexpectedly.
Can someone explain what happened ?

Thank you very much !

---

### Post by P4man on 2009-10-20
Im just guessing here, but the error you got relating to ACPI makes me think its a problem with the bios, possibly triggered by a newer kernel that you havent installed yet now. 

Perhaps you can check if there is a newer bios available for your machine, and it wouldnt hurt to post the output of dmesg here as attachment, perhaps it gives a clue already.

---

### Post by akavinski on 2009-10-20
Here is dmesg copy-paste that I get from new installation.
Now I user ext4 as fs, and latest kernel via update and yet it works well (like previous instalation). I'm really a noob to linux so I might write some nonsences, but I like it and want to dig deeper into.

Thanx for your time !

---

### Post by P4man on 2009-10-20
I cant see anything terribly wrong in that dmesg. Only problem i see is > Clocksource tsc unstable (delta = -189311371 ns)
Ive seen that all too often with crappy motherboards, but its not necessarly a problem. should you ever get random lock ups, keep that in mind though.

Googling on the error you previously had also sheds precious little light on the matter. I guess it could be anything from a dying harddisk, a BIOS problem or a bug, However, I did see people who reported the same error, reinstalled like you, only to have the problem returning after some weeks, so i wouldnt be very confident.

I guess it wouldnt hurt to run a memory diagnostics program (there is one on the ubuntu live cd) for several hours and if possible, a harddisk diagnostics program. *The ultinate boot cd* has harddrive diagnostic programs for every common brand, google on it  to find it.

---

### Post by akavinski on 2009-10-20
Thank you very much P4man !

I forgot to mention that I'm running ubuntu (and beside w7 as dualboot) on a MSI 720EX laptop, I bought it 2-3 months ago.

On w7 there are no problems at all (exept I will have to pay it in a future). Ubuntu gives me everything I need for work (Komodo edit, Code Blocks, XAMPP,OpenVPN, etc..) and yet I did not find any stability problems exept this. I cant afford to lose months of work and this frithened me a lot.

I will run through tests (memory and HDD) though I really doubt that there is a problem.

And one thing I forgot - On my lap is x86 version, I tried 64bit but with no success establishing openVPN and many bugs that it had.

Thanx again for your help !

---

### Post by P4man on 2009-10-20
> **akavinski said:**
> I cant afford to lose months of work and this frithened me a lot.

Of course you cant. that why you make backups. I hope :)
You should also consider setting up a seperate /home partition so if ever you do a fresh install, or want to try another linux or ubuntu, you dont have to format your data in /home.

---

