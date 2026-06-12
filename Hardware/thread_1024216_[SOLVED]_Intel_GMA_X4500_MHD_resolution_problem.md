---
title: "[SOLVED] Intel GMA X4500 MHD resolution problem"
date: 2008-12-28
forum: Hardware
---

### Post by m4lte on 2008-12-28
SOLVED

Hi there!

I just installed Ubuntu 8.10 on a Thinkpad R400 with a built in GMA X4500 MHD.
In Windows I used a "native" resolution of 1280x800. However, in Ubuntu the highest possible resolution is 1024x768. What do I have to do, in order to use a higher resolution?

I searched the forum and google, but I couldn't find any solutions. I'm new to Linux and there's a lot things I don't understand. Please explain slowly ;)

Thanks for any help!


// EDIT:
I found some help on this page: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
and I was able to temporarily change the resolution to 1280x800 using
  $ xrandr --output LVDS --mode 1280x800

Though, I'm still not sure how to change the resolution permanently. There's an example given, using xorg.conf, but I'm not sure what I'd have to write in my case. (Is there a page explaining the general concept of the xorg.conf?)
**Do you know how I can make 1280x800 the _default_ resolution?** I guess it would be fine to have a startup script, executing the command mentioned above? How can I do that?


// EDIT 2:
One time, after starting the computer, the resolution was automatically set too 1280x800 and the monitor was detected as 14" screen, but after another restart it was again set to 1024x768, and the monitor was titled "unknown" in the screen resolution gui tool.

// EDIT 3:
I solved the problem following this method:
[http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Internal_LCD_Resolution_Fix](http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Internal_LCD_Resolution_Fix)
and resetting my xorg.conf, using (i think) this line:
sudo dpkg-reconfigure -phigh xserver-xorg

---

