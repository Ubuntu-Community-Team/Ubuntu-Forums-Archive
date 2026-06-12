---
title: "Uninstall Ubuntu 8.10 and install Vista"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by saileunglau on 2009-04-14
Hi guys! Hope you can help me.

My Toshiba Satellite A135 with Vista Home Premium pre-installed crashed a few months ago. Out of curiosity, I tried Ubuntu to see if it works fine for me.

Now, with a Vista Home Premium disc in hand, I would like to install Vista back to my puter. But it turns out because my puter is running Linux, it doesn't boot from my Vista disc. I tried a few suggestions found from other forums but to no avail.

Can anyone please help guide me through this transition? I have all my personal file stored else where already. I gather (probably incorrectly) I have to do the following:

1. erase Ubuntu
2. install some OS that Vista can boot from
3. let the Vista installation disc take over

All suggestions are welcome! ;)

---

### Post by lisati on 2009-04-14
Is the Vista disk one you made for yourself using the tools that come with some Toshiba laptops, or is it one you bought?

EDIT: I just remembered: some time ago, I had Ubuntu on my Toshiba A100 laptop, and wanted to put XP back on it. The recovery DVD that came with the laptop didn't seem to want to work, until I renamed what was to become the C: drive to the original factory set volume label, which I found in file data.ini (in the root directory of the recovery disk) in a line which begins "SoftwareNumber="

---

### Post by ninjapirate89 on 2009-04-14
You just need to put the Vista cd in and restart your computer and hit F12 or whatever button it is on your computer to access the BIOS and change it to boot from cd.

Edit -> I looked up your computer type and it seems the button you press is F1 not F12. You will want to press this almost immediately after you computer starts.

---

### Post by saileunglau on 2009-04-14
> **lisati said:**
> Is the Vista disk one you made for yourself using the tools that come with some Toshiba laptops, or is it one you bought?

Hi **lisati**! I got the iso online and burnt it into a DVD awhile ago. I figured since I had Vista pre-installed and (still) have the product key in hand (well, under my laptop literally), it should be alright.

---

### Post by lisati on 2009-04-14
> **saileunglau said:**
> Hi **lisati**! I got the iso online and burnt it into a DVD awhile ago. I figured since I had Vista pre-installed and (still) have the product key in hand (well, under my laptop literally), it should be alright.

Be careful with Windows ISO files you get online: apart from potential legal hassles, there might be nasty surprises on it (in the form of malware - viruses etc)

Did you burn it as a "disk image"?

EDIT: Further homework (which can come later): "Standard" Windows disks don't always come with all the drivers you might need. Check [www.toshiba.com](www.toshiba.com)

---

### Post by saileunglau on 2009-04-14
> **lisati said:**
> Did you burn it as a "disk image"?

Yes, indeed!

---

### Post by lisati on 2009-04-14
My thoughts at this stage are check out the following (other forum users might have other suggestions as well):[LIST=1]
[*]Backup your important data
[*]Using the partition manager on an Ubuntu Live CD, delete the Ubuntu partition(s)
[*]Restart your computer and see if you can boot the Windows installation disk and get it working (ninjapirate89 recommended pressing F1 while you see the "Toshiba" screen and telling the computer to boot from CD, there's usually something displayed at the bottom of the screen.)
[/LIST]

---

