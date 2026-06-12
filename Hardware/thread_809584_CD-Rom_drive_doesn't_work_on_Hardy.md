---
title: "CD-Rom drive doesn't work on Hardy"
date: 2008-05-27
forum: Hardware
---

### Post by dgeleyn on 2008-05-27
Hello,

I'm working on Xubuntu for about 2 weeks now, and I like it very much, but I have one very strange problem. The cd-rom drive does not load audio cd's, but it does load regular data cd's. Anyone who has a solution for this problem ?
I work on a Compaq Armada E500 with Xubuntu 8.04. My kernel version is 2.6.24-16-generic. I don't know how to look of which type my cd-drive is (I'm only a beginner..)

Thanks in advance
Dennis

---

### Post by fred.warren on 2008-08-02
Hi I just solved this problem myself and will be filing a bug report.

Thunar has the association for audio cds cdda:/ instead of the proper cdda:// and for dvds as dvd:/ instead of dvd://

To correct this do the following
[LIST=1]
[*]Open Thunar (Can be found on the Menu under Accessories)
[*]From the menu at the top of Thunar select **_E_dit**
[*]From the **_E_dit** menu select **Pr_e_ferences**
[*]From the **File Manager Preferences** dialog, click on the tab labeled **Advanced**
[*]From the **Advanced** tab click on the blue linked word **Configure**
[*]From the **Removable Drives and Media** dialog, click on the tab labeled **Multimedia**
[*]From the **Multimedia** tab for the **Audio CDs _C_ommand** locate the entry **totem cdda:/**
[*]Change that to **totem cdda://**
[*]From the **Multimedia** tab for the **Video CDs/DVDs C_o_mmand** locate the entry **totem dvd:/**
[*]Change that to **totem dvd://**
[*]Close all dialogs and exit Thunar
[*]Insert your CD or DVD and enjoy
[/LIST]

---

### Post by kismul on 2008-10-26
> **dgeleyn said:**
> Hello,

I'm working on Xubuntu for about 2 weeks now, and I like it very much, but I have one very strange problem. The cd-rom drive does not load audio cd's, but it does load regular data cd's. Anyone who has a solution for this problem ?
I work on a Compaq Armada E500 with Xubuntu 8.04. My kernel version is 2.6.24-16-generic. I don't know how to look of which type my cd-drive is (I'm only a beginner..)

Thanks in advance
Dennis

Also a newbie, I have virtually the same config as Denis and a variant of the same problem. I've just done a full install of xubnutu 8.04.  Prior to this, I had Ubuntu installed but it was so slow that I decided to give xububtu a try.  The variation is that there is no recognition by xubuntu that a CD drive exists.  On the desktop, there's no CD icon.  Should there be?

With Ubuntu, everything worked, including playing CDs with Kaffeine.  Now, although brasero appears to read and copy discs, totem refuses to see them.  Instead I get "Location not found".  And I can't see the drive in Thunar.  Although I may just be looking in the wrong place.

Desperately in need of advice - HELP!

PS I did try the suggested edit to preferences but it didn't help.

---

