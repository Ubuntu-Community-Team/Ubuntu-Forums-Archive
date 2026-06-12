---
title: "Ubuntu 10.4 on Asus 1005pe back light issues and other function keys partly solved"
date: 2010-05-22
forum: Hardware
---

### Post by Hansmc on 2010-05-22
I just up graded my Asus 1005pe to Ubuntu 10.4. After upgrade none of the function keys worked except the wireless. The screen back light keys would adjust the back-light but in a random way and was never very bright. However, it did show a little scrolling bar, as I would press fn + F5 or F6.

After looking around quit a while I found: [http://ubuntuforums.org/showthread.php?t=1412922&highlight=backlight+asus&page=2](http://ubuntuforums.org/showthread.php?t=1412922&highlight=backlight+asus&page=2)

Basically the part that helped was:
> 
this will make the brightness keys work:
sudo gedit /etc/default/grub

Find the line GRUB_CMDLINE_LINUX_DEFAULT and add "acpi_osi=Linux" so it looks like this GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux". Save the file. Now run update-grub2.

sudo update-grub2

But gnome power manager still randomly changes the backlight. I disabled it from startup, and start it from the command line when i want to suspend on closing the lid.


As noted the back-light does randomly change and I am not sure how to stop that and I do not want to have to run some command to suspend. So I am just going to leave it for now. Hopefully someone will have a fix for that some time soon.

Interestingly, the above command also made the sleep button, the touch-pad on/off button, and the volume buttons work. There is still a few buttons that do not work.

However, when brightening and dimming the screen there is no indicator in the upper left hand corner like there use to be. The screen off button still does not work. It never has.

Maybe this will help someone else, and maybe someone will be able to help me with the last few issues. The random changing of the back light is the biggest thing. Thanks

---

### Post by Hansmc on 2010-05-22
I added "acpi_backlight=vendor" to the /etc/default/grub file, and now when brightening and dimming the screen there is an indicator in the upper left hand corner. The line in the file now looks like:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
```

Hopefully it also helps with the random changing of the back light. I will wait and see.

The screen off fn+F7 still does not work.

---

### Post by Hansmc on 2010-05-23
At this point it seems the random screen flicker was fixed by the last thing I added to the grup line. It took me about four hours of searching to find this fix, so I put it here and hopefully it will help someone else. 

The next thing on my list is to find out is if there is a way to fix the volume controller on the task bar. It no longer shows the volume adjustment as I scroll the mouse wheel on it, and the mouse wheel will not take it off of mute. Two features I really like from the last version of Ubuntu.

---

### Post by drkages on 2010-07-13
Thanks a lot for putting together this post. It has been a great help getting my 1005pe to work.

However I noticed that on my mouse menu that "two-finger scrolling" is disabled.

Is it similarly grayed out on your installation, any suggestions for fixes will be appreciated

thanks

---

### Post by dsurfer21 on 2012-02-01
I had a similar issue with my Asus UL20A and so far your method seems to have solved the issue.  Thanks so much!

---

