---
title: "Ubuntu 12.04 Cannot adjust brightness on Dell Inspiron 15 (3521)"
date: 2013-10-07
forum: Hardware
---

### Post by codinglinda on 2013-10-07
Dell Inspiron 15 (Inspiron 3521). The graphic card is the integrated Intel graphic card: Intel® HD Graphics
Screen is: LED Backlit Display with Truelife and HD resolution
Install Ubuntu 12.04 downloaded in Sep. 2013.
If I use the function key Fn+F4/F5, it shows the brightness bar. But there is not effect. The brightness stays the same.

I googled. 
One suggested solution to use grub: 
acpi_osi=Linux or acpi_backlight=vendor, 
You know there are many variants.
Then I restarted my laptop: after the menu, it is stuck there.
Then I can only force to turn off the laptop, and restart to choose the recover mode. Ubuntu will start. Brightness still cannot change.
I change the grub setting back. Now the laptop can start correctly.
Of course, brightness adjustment still does not work.
And actaully after several rounds of trying different variants to revise the grub, the Ubuntu system simply becomes ineffective. So I have to reinstall Ubuntu.

The second suggested solution is to install xbacklight.
It cannot work.

I used 
xrandr -q | grep " connected"
xrandr --output LVDS1 --brightness 0.8
it seems to work. But I think it adjusts not brightness, but contrast. So actually it looks not good.



Then what should I do?
Now I do not want to use the newly bought Dell laptop any more. Or I switch to Window? Oh, I like Ubuntu! Now I feel very upset with the screen issue.

---

### Post by mike_kzc on 2014-01-14
I had exactly same problem, please help.

Mike

---

### Post by varunendra on 2014-01-15
Hello Mike !

Please try what is suggested in this post : [http://ubuntuforums.org/showthread.php?t=2170137&p=12769346#post12769346](http://ubuntuforums.org/showthread.php?t=2170137&p=12769346#post12769346)

If that doesn't help, or if you have trouble following the suggestions, I'd recommend to start your own new thread and post the details of the problem there. Along with the description, also post the output of the following code there :
```
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```
Feel free to post a link to your thread here if you start one.

---

### Post by mike_kzc on 2014-01-15
> **varunendra said:**
> Hello Mike !

Please try what is suggested in this post : [http://ubuntuforums.org/showthread.php?t=2170137&p=12769346#post12769346](http://ubuntuforums.org/showthread.php?t=2170137&p=12769346#post12769346)

If that doesn't help, or if you have trouble following the suggestions, I'd recommend to start your own new thread and post the details of the problem there. Along with the description, also post the output of the following code there :
```
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```
Feel free to post a link to your thread here if you start one.

Hi, Varunendra,

Thanks alot. I have followed what has been said in the suggested post, it does NOT work.

This is the output from yr code

************
**********************
 /sys/class/backlight/acpi_video0
99
99
99

 /sys/class/backlight/intel_backlight
574
4882
574
**********************************

Also, a new post was created here: [http://ubuntuforums.org/showthread.php?t=2199695&p=12901023#post12901023](http://ubuntuforums.org/showthread.php?t=2199695&p=12901023#post12901023)

Thanks again.

Mike
************

---

