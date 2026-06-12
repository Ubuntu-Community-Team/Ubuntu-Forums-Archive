---
title: "Removing ubuntu, installing vista, GRUB Error 17"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by teamsupreme on 2009-04-28
Hey. I was removing ubuntu from my Acer Laptop, and putting Vista back on it, but now it's showing GRUB Error 17. How do I get rid of GRUB once and for all?

---

### Post by gohanssjn on 2009-04-28
Boot from your Vista disk and do a "Start-up repair."  It should reinstall the Vista BCD.

---

### Post by teamsupreme on 2009-04-28
Yeah...my recovery disc only is letting me restore it to factory defaults. I tried that, and GRUB still lingers...

---

### Post by gohanssjn on 2009-04-28
Ok, give me 2min, and I can find aguide for you that will force a re-write.

---

### Post by teamsupreme on 2009-04-28
Sweet. Thanks.

---

### Post by gohanssjn on 2009-04-28
> To run the Bootrec.exe tool, you must start Windows RE. To do this, follow these steps:

   1. Put the Windows Vista installation disc in the disc drive, and then start the computer.
   2. Press a key when you are prompted.
   3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
   4. Click Repair your computer.
   5. Click the operating system that you want to repair, and then click Next.
   6. In the System Recovery Options dialog box, click Command Prompt.
   7. Type Bootrec.exe, and then press ENTER.

Then type and run:
Bootrec.exe /RebuildBCD
Bootrec.exe /FixBoot

That should do it for you.

---

### Post by teamsupreme on 2009-04-28
I'm afraid this won't help. I recieved a recovery disc for my Acer Laptop. It came with 3 discs. All it does is restore the computer to it's factory defaults. I had to remove ubuntu with a GParted Live CD. It's not a typical Vista Installation CD. Also, there is no Command Prompt option, only restore to factory defaults.

---

### Post by gohanssjn on 2009-04-28
Ah, I see what you mean.  Unfortunately, I am unfamilure with any way to do it without a Vista DVD.

Wait, I have an idea.  Vista is still installed, correct?

Load your Ubuntu LiveCD, choose boot from first harddisk.  This should load Vista.  Then download EasyBCD.  That should allow you to rewrite the BCD from within Vista.

---

### Post by teamsupreme on 2009-04-28
Okay. I just have to redownload the Ubunty 8.10 ISO. Hurray!

EDIT: What do I edit when using EasyBCD?

Okay...GRUB still won't let me do it...now what?

---

### Post by gohanssjn on 2009-04-28
There should be an option in EasyBCD to re-write the BCD under "Manage Bootloader".

If that does not work...then your boot flag is set to the Ubuntu partition.  Load the LiveCD, go to System -> Administration -> Partition editor and make sure your Vista partition has the boot flag.

---

### Post by Ptero-4 on 2009-04-28
Can you use the ms-sys tool (you get it off packages.ubuntu.com since the last version was for dapper). It should allow you to put a M$ compatible boot sector.

---

