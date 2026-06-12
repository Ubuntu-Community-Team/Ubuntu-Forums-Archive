---
title: "screen resolution"
date: 2008-09-25
forum: General Help
---

### Post by ron101 on 2008-09-25
I have winxp sp2 on C drive and UBUNTU on J drive installed with WUBI all went fine but now when im in ubuntu i find i have only 2 choices of screen res. 800x600 and 640x460 i think, i run windows at 1280x800, I cant find a way to reduce it any more, even 1075 would do, can you help?

---

### Post by billythekid on 2008-09-25
see if your monitor is listed in the system settings/monitor window.

Once I found my monitor all the available options were right there.

If your monitor is not listed you'll need to edit a .conf file(X11.conf I think)

---

### Post by WWSmith36 on 2008-09-25
I recommendation install a normal dual version of ubuntu rather than windows.  If you have problems with your windows partition you will damage it can damage you ubuntu system as well.

Anyway,

Try to use displayconfig-gtk: Simple gtk tool to change xserver settings like graphics card driver or monitor.

-- Please open a Terminal from the menu Applications->Accessories->Terminal and type or better copy and paste:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install displayconfig-gtk

-- give your user password when requested, you don't see nothing when you type it, then press enter.

Then to configure your monitor resolution:

sudo displayconfig-gtk

Afterwards, reboot

Hope this helps

---

### Post by ron101 on 2008-09-25
Thanks ive done it anyway now thanks for returning the calls.

---

### Post by Sockerdrickan on 2008-09-27
reboot and choose recovery mode, choose xfix then continue

---

### Post by gjoellee on 2008-09-27
> **Tux0r said:**
> reboot and choose recovery mode, choose xfix then continue

+1 for a little more detailed info use this link: [http://www.kshoster.net/node/18](http://www.kshoster.net/node/18)

---

