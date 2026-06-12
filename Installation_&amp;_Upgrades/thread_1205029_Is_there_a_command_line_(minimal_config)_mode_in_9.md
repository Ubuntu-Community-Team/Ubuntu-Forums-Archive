---
title: "Is there a command line (minimal config) mode in 9.04?"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by jg167 on 2009-07-05
Some revs ago one thing I really liked about Ubuntu (if I am recalling correctly) was that at install time you could select between server, desktop, and minimal.  This was really handy to be able to put a minimal install on the CF card in my bot but also have a culturally compatible desktop on an external disk I can plug in for development when the bot is in the shop so to speak.  I switched to Fedora a while back as I was using it elsewhere but its just to big for my tiny robot (mini-itx based with 4G compact flash).

When did that go away and get replaced by different CD versions?  e.g. is it still in Ubuntu 8?

But ok, different CD images, I can live with that inconvenience.  So I used the alternate CD iso image to try and get the minimal version (what now seems to be called command line mode) but was offered no such choice and got a full gnome desktop with all the usual daemons.  It did sucessfully install and does run on my small system (1Ghz PIII, 256MB, 4G) but there is still way too much stuff.  Its so much easier to add things little by little as needed (and have the dependencies managed) then to try and take them away.

Did this command line mode of the alternate CD also go away with 9.04?  (or if this experience is not expected for 9.04 maybe the mirror I picked has its iso's confused and is offering the desktop image labeled as alternate???)

I see Xubuntu is also related to this issue, but the alternate command line vesion of Ubuntu seemed like it should have worked for me (than I can add a minimal X setup). Do I have to start with a special Xubuntu iso to get this?

---

### Post by Cheesemill on 2009-07-05
I'm pretty sure the CLI install option on the alternate CD doesn't install a GUI. But if you're still having problems then try using the mini CD image:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It's only 10MB as it downloads the most up to date versions of packages during the install. This means you have a fully updated system as soon as the install is finished. It also lets you install a CLI only system.

I use this installation method myself followed by the following command to get a desktop install thats around 1GB and then add apps as I need them from there:
```
sudo apt-get update && sudo apt-get -y install xorg && sudo apt-get -y install gdm gnome-core ubuntu-artwork fast-user-switch-applet usplash usplash-theme-ubuntu && sudo shutdown now -r
```

---

### Post by jg167 on 2009-07-05
> **Cheesemill said:**
> I'm pretty sure the CLI install option on the alternate CD doesn't install a GUI. But if you're still having problems then try using the mini CD image:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)OK, but what "CLI install option" is that?  I did not see any such option even after I turned on "expert mode".

> **Cheesemill said:**
> 
It's only 10MB as it downloads the most up to date versions of packages during the install. This means you have a fully updated system as soon as the install is finished. It also lets you install a CLI only system.I don't care about the size of the downloaded media, I care about the size and complexity (daemons etc) of the resulting installed system.

---

