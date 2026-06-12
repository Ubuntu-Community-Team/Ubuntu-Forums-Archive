---
title: "Will it work?"
date: 2012-01-08
forum: Hardware
---

### Post by SterLu on 2012-01-08
Well I've been using XP for a while now and I want to make a dual boot with Ubuntu, my question is- will I have any problems and will it run smooth on my specs? 
I'm running a Amd Athlon xp 2400+ @ 2Ghz with 1.5Gb RAM and an nVidia FX 5200 graphic card
Oh, and are there any disadvantages or risks with dual boot?

---

### Post by mikewhatever on 2012-01-08
It will work if you do it right.

---

### Post by F.G. on 2012-01-08
i think it should work, although you can always try running it as a live cd/usb first. also as far as i'm aware there is no disadvantage to dual booting.

ps isn't this a support question?

edit -> oops, thought this was in the cafe.

---

### Post by jerrrys on 2012-01-08
You have the specs to run Ubuntu.  You may find it has a bit lag on a single core.  If so, there is always Xubuntu, which was design for older computers and in my opinion, an excellent choice.

Also be sure to have a windows restore disk.  Its needed to restore windows if you decide to remove ubuntu.

---

### Post by SterLu on 2012-01-08
> **jerrrys said:**
> Also be sure to have a windows restore disk.  Its needed to restore windows if you decide to remove ubuntu.

What do you mean? I tought I could just simply remove it, I've read somewhere that uninstallation goes just like removing an application, through XP's "Add of remove programs"

---

### Post by JRV on 2012-01-08
> **SterLu said:**
> What do you mean? I tought I could just simply remove it, I've read somewhere that uninstallation goes just like removing an application, through XP's "Add of remove programs"

That is true for a WUBI installation.  Is this what you have planned?

---

### Post by SterLu on 2012-01-08
> **JRV said:**
> That is true for a WUBI installation.  Is this what you have planned?
Yup, if I install with Wubi it won't affect Windows, right? I don't need that restore disk?

---

### Post by Mark Phelps on 2012-01-09
If you're worried about not being able to restore Windows, then make an offline backup using the FREE version of Macrium Reflect.  

You can download that, run it in Windows, and image off your Windows setup to an external drive.

If you then use the option to create a Linux Boot CD, you could use that later to restore Windows from the backup.

---

### Post by Basher101 on 2012-01-09
> **SterLu said:**
> Yup, if I install with Wubi it won't affect Windows, right? I don't need that restore disk?

a WUBI install will not affect your bootloader, thus you wont need a restore disk to restore it after you delete it when doing a WUBI install. WUBI is the best way to check it out before making a real install. The only disadvantages are:
 - if windows' bootloader gets corrupted, you cant access Ubuntu and
 - speed, but you wont really take such a big notice when using a WUBI install...

---

