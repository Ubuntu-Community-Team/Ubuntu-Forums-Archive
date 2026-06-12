---
title: "Blackscreen after login: Lenovo Z710, Ubuntu 13.10 (updated)"
date: 2013-12-09
forum: Hardware
---

### Post by helasraizam on 2013-12-09
Well, I finally did it.  I'm dual booting Windows 8 and Ubuntu 13.10 on a gpt filesystem with UEFI, based on several pages now deep in my bookmarks.  Well, I actually did that last week.  What I've been spending the last five days on is getting Ubuntu to work.

It works in its initial setup, but who can go without getting the latest upgrades?  Every time I do this, upon login I'm greeted with the ever-familiar "Something's gone wrong--report to Canonical?", windowless (no x - []), with a black background and only a cursor to keep me company.  I've done everything within google reach--I tried gdm, ubuntu2d, gnome, lightdm again--I even went so far as to patch an nvidia driver before realizing that the more up-to-date one doesn't need patching (though pre-install still fails).  I'm currently in this situation, under lightdm and gnome, with NVIDIA 331.20 (again, successful install, unsuccessful pre-install), having purged nvidia* and nouveau*.  So let's do this.  I'll be around all day.  I'm obviously doing everything through ctrl+alt+F3's terminal.  My laptop is Lenovo's Z710 with Optimus, NVIDIA GeForce GT 745M: [Specs]("http://www.staples.com/office/supplies/StaplesProductDisplay?storeId=10001&langId=-1&krypto=MxxBA%2BljVh6J4ByPRyWDNCKhOzthzxKeorqS0GEvSIYIxMoFBT%2FWFEjnoLlPHz1xWnxOTD7rut7X%0AsYlZMgS%2BVNdhznSYAQulWjGpQT8Lc6paEnw958TQYQ%3D%3D").  I've disabled windows fast startup and secure boot through bios, UEFI enables legacy (but I checked at one point in the last four days and Ubuntu should be booting EFI).

EDIT: I should also mention I added nomodeset to the grub boot params, or the screen would be black before the login.

TL: DR; Z710 blackscreens after login.

---

### Post by helasraizam on 2013-12-13
I've installed the latest NVidia in the repos (319-current), bumblebee, primus, and bumblebee-nvidia.  Now instead of a black screen I see my desktop image after logging in--still no window manager.  Can someone ask me to upload some logs so that we can see what's wrong?  I need a keyword to go off of.

Thanks!

---

### Post by aosipov.me on 2014-01-02
[h=3]Ubuntu 13.10 desktop - can't install on Lenovo Z710[/h]I created bootable usb, can see text menu at the beginning, and then black screen
please help

---

### Post by pail on 2014-01-06
I don't know a whole lot, but I've got Ubuntu running on a Lenovo Z710 (albeit without Windows) so I can at least tell you things I had to do to get mine working.

I have a black screen after grub every time.  This is just the initial brightness setting being all the way down, I am able to turn up the brightness and proceed normally.  Have you tried this, without the nomodeset parameter?

Also, if you don't particularly need the nvidia card in ubuntu you can disable it in the bios.  This saved me a lot of headache with the drivers, and it's not a huge deal to turn it back on when booting to windows.  

Hope any of that helps.

---

### Post by Dr. McKay on 2014-01-28
> **pail said:**
> I don't know a whole lot, but I've got Ubuntu running on a Lenovo Z710 (albeit without Windows) so I can at least tell you things I had to do to get mine working.

I have a black screen after grub every time.  This is just the initial brightness setting being all the way down, I am able to turn up the brightness and proceed normally.  Have you tried this, without the nomodeset parameter?

Also, if you don't particularly need the nvidia card in ubuntu you can disable it in the bios.  This saved me a lot of headache with the drivers, and it's not a huge deal to turn it back on when booting to windows.  

Hope any of that helps.

Does the keyboard backlighting work in Ubuntu ?

---

