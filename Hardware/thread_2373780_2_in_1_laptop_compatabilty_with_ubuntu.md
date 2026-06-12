---
title: "2 in 1 laptop compatabilty with ubuntu"
date: 2017-10-09
forum: Hardware
---

### Post by noam4 on 2017-10-09
I am looking towards buying a 2 in 1 laptop (with touchscreen and rotation) and install ubuntu on it, but I am having trouble finding out if Ubuntu can be installed on those laptops and if all of the hardware will work. I was looking at:
[URL="http://store.hp.com/us/en/mdp/laptops/spectre-x360-211501--1"]
HP spectre x360[/URL]
[URL="https://www.samsung.com/us/computing/windows-laptops/notebook-series-9/notebook-9-pro-13--np940x3m-k01us/#specs"]Samsung notebook 9 pro
[/URL][URL="https://www3.lenovo.com/us/en/laptops/yoga/700-series/Yoga-720-13/p/88YG7000827?menu-id=Yoga_720_(13%22)"]Lenovo Yoga 720
[/URL]
Have anyone any success with Ubuntu on this laptops?
The info on the web seems to be very partial.

Thanks

---

### Post by helotbc-0 on 2017-12-26
I just bought a Lenovo Yoga 720 and have been unsuccessful in installing Ubuntu 16 or 17. The installer doesn't seem to detect the harddrive (SSD). -Brendan

---

### Post by helotbc-0 on 2017-12-27
By default, in BIOS the disk is set to RAID. I set it to ADHI and the Ubuntu loader worked successfully. Windows would not boot (I was attempting to set up a dual boot machine). Neither OS booted when switching back to RAID.

---

### Post by gontijo on 2017-12-28
Haven't tried none of those in your list, but I did have an Acer Spin 5 and can report that everything works out of the box.

---

### Post by tokyobadger on 2017-12-29
@helotbc-0: it seems you need some extra steps to make sure that Windows remains bootable
[https://askubuntu.com/questions/946480/installing-ubuntu-alongside-windows-on-lenovo-yoga-720](https://askubuntu.com/questions/946480/installing-ubuntu-alongside-windows-on-lenovo-yoga-720)

---

### Post by helotbc-0 on 2018-01-20
When I booted to Windows, after changing the HD to AHCI, Windows choked. Then it did an automatic diagnostic and eventually booted. No crisis.

---

