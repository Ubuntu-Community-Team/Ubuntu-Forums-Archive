---
title: "selected wrong graphics card"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by lunamystry on 2007-11-14
i bought a new monitor and i was busy setting it up when i decided to just look at the graphics card tab. i went through the list and then closed the screen settings thing. i then logged out and when i logged back in i was told ubuntu was running in low graphics mode and i was to select my graphics card and monitor. i don.t know my graphics card but i dont think i have one. anyway now my screen is all messed up i can.t see anything from the login window. i can log into kde ubuntu which is on another hard drivd and it works fine. how do i change my graphics card settings? i dnt have a dedicated graphics card but i have 512 ram.

---

### Post by taurus on 2007-11-14
You have one of those onboard graphic card controllers.  It's probably an Intel but you need to check to be sure of that.  You can run this command from a terminal to see what it is.

```
lspci
```
And if you need to reconfigure your X server, just run

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by lunamystry on 2007-11-14
Thank you very much. I logged into failsafe mode on startup and i ran the commands given and after a lot more than a few questions in my lazy opinion i got it working.

---

### Post by taurus on 2007-11-14
As long as it's working in the end, it all matters.

---

### Post by lunamystry on 2007-11-15
okay i think i did something wrong while configuring the xserver or something. After using my pc for a while i get errors with whatever i try to open. And the icons show like a white paper with a red x and the cursor also changes.

---

### Post by xeth_delta on 2007-11-15
> **lunamystry said:**
> okay i think i did something wrong while configuring the xserver or something. After using my pc for a while i get errors with whatever i try to open. And the icons show like a white paper with a red x and the cursor also changes.

Could you please open a console / terminal and check if there is a back-up of your /etc/X11/xorg.conf file? Maybe you can recover the old configuration you had and just replace the video card driver for the correct one.

Xeth

---

### Post by lunamystry on 2007-11-15
I went to the /etc/x11 folder via nautilis and i found that i have 14 xorg.conf i looked at my kubuntu installation which i haven.t done much to only has four. there is none marked backup

---

### Post by xeth_delta on 2007-11-23
> **lunamystry said:**
> I went to the /etc/x11 folder via nautilis and i found that i have 14 xorg.conf i looked at my kubuntu installation which i haven.t done much to only has four. there is none marked backup

Depending on how nautilus is configured it might not show you all the files (for example hidden files starting with a dot) or all the details.

Please go to that directory on a terminal and look at the contents

```
cd /esw/X11
```
```
ls -al
```

Back-up your current xorg.conf file, then you can edit it:

```
sudo cp xorg.conf xorg.conf-bkp
```
```
sudo nano xorg.conf
```

Xeth

---

