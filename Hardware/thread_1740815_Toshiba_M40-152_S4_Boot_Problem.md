---
title: "Toshiba M40-152 S4 Boot Problem"
date: 2011-04-27
forum: Hardware
---

### Post by Fightback on 2011-04-27
Hello Guys

I have just gotten a (really) old laptop from my brother, who got it from our dad a while ago... A Toshiba M40-152 S4 ([Specs]("http://ch.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?LNG=8&service=CH&PRODUCT_ID=104377&DISC_MODEL=1"))
Anyway, of course my first action was to install Ubuntu 10.10 from a disk coming with a book, [This]("http://www.galileocomputing.de/katalog/buecher/titel/gp/titelID-2521") one. I checked the disk before installing, it is fine.
After it finished installing, which it did without any errors or such, I rebooted in the normal mode, and the only thing that is visible is the mouse cursor and the wallpaper. I can move the mouse normally.
I then have to hard reboot (=press the powerbutton until the screen blacks out). If I restart the laptop, and chose the Safe Mode from the screen where I can chose the account, the laptop starts up normally.
I then tried out the recovery mode that you can access from the GRUB. There is something quite suspicious there, because there is an error report in the menu, saying, instead of Resume normal boot (or something like that, just the first item on the list), ```
[    21.560280] AC'97 access is not valid [0xffffffff], removing mixer.
[    21.560332] Unable to initialize codec #1
```What I already did is that I did sudo update and upgrade, which was the first response to a lot of other problems. Didn't help.
When I played around with the command line a litte, there was also a Gtk error.
I hope you can help me, since I'd really like to use this laptop with ubuntu.

---

### Post by Fightback on 2011-04-28
Issue has resolved itself. Ubuntu checked the disk (automatically, I didn't do anything) and when I then tried to boot in normal mode, it just worked.
What might have been important too (or maybe not) is that I changed the wallpaper. Because when I tried to boot in normal mode it seemed almost as if it would just stay blank again, but then the wallpaper changed and then the menus from gnome blended in.
Now upgrading to 11.04, I shall edit this post after the completion of upgrade about the results.

---

