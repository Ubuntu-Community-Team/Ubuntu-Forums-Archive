---
title: "Wubi installer downloading wrong version"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by hyderalamgir on 2009-04-24
My system's a core 2 duo intel running XP right now.
I'm trying out ubuntu, in fact, my first linux experience.

Now, I downloaded ubuntu-9.04-desktop-i386, when i try running the installer, it starts downloading ubuntu-9.04-desktop-amd64... why is that?

Also, what does installation size refer to?

---

### Post by suprecook on 2009-04-24
It might be doing that if you have windows 64 bit installed. If that's not the case try downloading wubi from another place. Or download the iso, burn it onto a disk and run wubi from that.

---

### Post by hyderalamgir on 2009-04-24
I don't have any blank CDs to burn it on, only DVDs, can I burn CD isos into a DVD? Nero wouldn't let me.

My Windows came bundled with the system and the processor is a 64 bit processor. I couldn't find a way to know if my Windows is a 64 bit or a 32.

---

### Post by hyderalamgir on 2009-04-24
Correction I have a 32 bit windows... confirmed.

I downloaded from ubuntu's site itself, not a torrent, direct download, my net is a 3G so it's slow.... I'd prefer not to have to download it again.

---

### Post by hyderalamgir on 2009-04-24
Please... someone... which ubuntu version do i download?

---

### Post by m_2009 on 2009-04-24
You could try renaming the ubuntu-9.04-desktop-i386 file to ubuntu-9.04-desktop-amd64 and then run wubi???

Not sure if it will work, but it could possibly trick wubi into thinking it already has the correct file...

---

### Post by hyderalamgir on 2009-04-24
Nope, doesn't work

---

### Post by Partyboi2 on 2009-04-24
> **hyderalamgir said:**
> I don't have any blank CDs to burn it on, only DVDs, can I burn CD isos into a DVD? Nero wouldn't let me.

My Windows came bundled with the system and the processor is a 64 bit processor. I couldn't find a way to know if my Windows is a 64 bit or a 32.
You can burn the iso to dvd, you can use a program call [[COLOR=Blue]imgburn[/COLOR]]("http://www.imgburn.com/") to burn the iso.
If you need to find out if you are running 32bit or 64bit xp you can do one of these methods

> **Method 1**
 
[LIST=1]
[*]Click **Start**, then click on **Run** or **Start Search**.
[*]Type **msinfo32.exe** and then press **Enter** key.
[*]In “System Information”, review the value for the **System Type** item:
[LIST]
[*]For 32-bit editions of Windows, the value of the System Type item is **x86-based PC**.
[*]For 64-bit editions of Windows, the value of the System Type item is **x64-based PC**.
[/LIST]
 
[/LIST]
 **Method 2**
 
[LIST=1]
[*]Click **Start**, click **Run**, type **sysdm.cpl**, and then click **OK**.
[*]Click the **General** tab. The operating system appears as follows:
[LIST]
[*]For a 64-bit version operating system: **Microsoft Windows XP Professional x64 Edition Version <Year>** appears under System.
[*]For a 32-bit version operating system: **Microsoft Windows XP Professional Version <Year>** appears under System.
[/LIST]
 
[/LIST]


---

### Post by hyderalamgir on 2009-04-24
Thanks, I'll try that DVD Burner.

And it is a 32 bit Windows... for sure now

---

### Post by m_2009 on 2009-04-24
Do you have the wubi.exe file and the ubuntu-9.04-desktop-i386.iso file in the same folder??

and you havent extracted the iso contents, it is still the full 700MB ISO file??

---

### Post by Partyboi2 on 2009-04-24
Another thing you could try is to put the ubuntu-9.04-desktop-i386 and the wubi.exe into the same folder and run the wubi.exe but make sure you have disconnected first from the internet.

---

### Post by m_2009 on 2009-04-24
> **hyderalamgir said:**
> I don't have any blank CDs to burn it on, only DVDs, can I burn CD isos into a DVD? Nero wouldn't let me.

My Windows came bundled with the system and the processor is a 64 bit processor. I couldn't find a way to know if my Windows is a 64 bit or a 32.

You dont need to burn the ISO to a CD/DVD. Wubi can install ubuntu using the downloaded ISO file directly.

---

### Post by hyderalamgir on 2009-04-24
Ahhh yes, I placed the ISO in the folder extracted from that ISO and now it works... thanks guys!

---

