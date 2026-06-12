---
title: "Installing Ubuntu 8.04"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by wisedrunkard on 2009-10-03
I just wiped a friends computer and put Ubuntu 7.10 on it, with the intention of upgrading 8.04.  However, whenever I put my Ubuntu 8.04 CD in, it hits a screen and I don't know what to do next.  The screen reads:

-----------------------------------------------------------------
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

-----------------------------------------------------------------

Any help would be greatly appreciated as google has yielded little.

---

### Post by friv_livs on 2009-10-03
Are you booting to a live run or install?

Did the md5sum return clean when you tested the .iso?

---

### Post by wisedrunkard on 2009-10-03
I am booting a live cd.  The screen pops up immediately after selecting the language to install in.  Nothing starts installing.  Thanks for the help

---

### Post by friv_livs on 2009-10-04
Sounds like a bad iso burn.

Try burning to DVD as it has a lower burn rate when burning.

If that doesn't work try downloading a fresh .iso and burning that to DVD at slowest burn rate.

---

### Post by rreese6 on 2009-10-04
Sounds like a bad CD.

Here are some steps to help you determine if everything is ok.

**ISO File Check**
1. make sure the ISO file has the correct MD5
you can do that in terminal.
Change directory to where the ISO is located then
```
md5sum <filename>.iso
```
that will return a line with along number in the first column.
compare that number to the number found on this page for the ISO you are using:
[https://help.ubuntu.com/community/UbuntuHashes#8.04%20LTS]("https://help.ubuntu.com/community/UbuntuHashes#8.04%20LTS")

or if you have one of these ISOs I have included a list here:
```
371bd54267de6169a602bd1fafa2abfd *ubuntu-8.04.3-alternate-amd64.iso
7a729db496ce2f8a84fb6f3927398066 *ubuntu-8.04.3-alternate-i386.iso
d7ba336d05045aa60d1114da686e6359 *ubuntu-8.04.3-desktop-amd64.iso
419b20ff1066f436dc9705fc09de9d3b *ubuntu-8.04.3-desktop-i386.iso

```

2. If the ISO is bad, download it again, then run through the above step again.

**CD CHECK**
3. Now let's check you copy of your CD
 You can check the integrity of the CD without rebooting as follows.
```
md5sum /dev/cdrom

```
you may need to change "cdrom" to cdrom0 or cdrom1 to make it work.
compare that output to the numbers above or on the website I gave you..

4. If the ISO file is good, but the CD is bad:
 Burn the ISO file to the CD using 4x or 8x...as slow as you can.

5. After you do a slow burn, go back to step 3 to verify it.

**To Be SURE CD is Good**

6. Once you boot up the CD, you can also run "Check CD Media" from the menu... if this passes then you know you have everything ready to install.

**Verify the Computer is Compatible With 8.04LTS**

7. Choose the First option (basically just hit enter when the menu comes up) to try Ubuntu without installing.(LiveCD Operation).
if this works, then you can just choose install from the desktop to complete the installation.
8 reboot and enjoy..

---

