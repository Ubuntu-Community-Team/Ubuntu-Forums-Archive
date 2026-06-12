---
title: "Remember Brightness on HP Pavilion DV6?"
date: 2010-06-07
forum: Hardware
---

### Post by bmach on 2010-06-07
Hi Everyone,

I've done a fair bit of searching on this one. It seems lots of other people have problems around laptop screen/display brightness but there's lots of threads out there unanswered. So I thought I'd try my luck.

So I have my new HP DV6 Pavilion laptop with Ubuntu 10.04 and everything is going nicely. Loving not being dependent on Windows. But everytime I reboot the laptop the brightness gets reset to it's dimmest. I can up the brightness to maximum quite easily using the adjustment keyboard keys Fn-F3 (up) and Fn-f2 (down) but they aren't sticky. The brightness applet slider and the brightness slider in power management options all have no effect on the brightness.

Any idea how I can make the brightness sticky (remembered) between boots?

Pressing my function keys must change some underlying config file I assume?

---

### Post by Gingerman on 2010-06-07
I'm just jumping in with a "Me Too."  This is the case for me in Kubuntu (KDE) on my Thinkpad.  I have to pump up the brightness every boot.

There is another display problem as well:  it rolls sometimes.  The screen just starts scrolling and won't stop.  This doesn't happen in Gnome.

There seems to be a screen problem in the KDE version.

---

### Post by bmach on 2010-06-07
Your rolling screen issue makes my brightness problem seem much smaller :) I definately done have that problem with gnome. 

I've just had a thought - is it possible our display brightness is adjusted by BIOS and not Ubuntu/kubuntu when we pump up the brightness using the FN keys? When my laptop boots the brightness is fine atthe grub menu. Pretty much as soon as ubuntu starts loading the display brightness drops to it's dimmest. But even before the OS has fully loaded (prior to login screen) I can use the FN keys to pump up the brightness.  That makes me think the OS isn't even controlling the brightness for me. Or maybe it just means X11 is loaded 1st which is why the keys work so early.  

Having said that the brightness in windows 7 is not a problem. So there must be some kind of setting in ubuntu/kubuntu to manage this?

---

### Post by bmach on 2010-06-08
Forget that Regarding the BIOS.. The FN keys do nothing while loading Win7 so it can't be BIOS... still hunting

---

### Post by acron1 on 2010-06-10
Similar problem here:
I have a Toshiba T115D-S1125 running Ubuntu 10.04, everything seems to be working fine, however every time I restart the OS the brightness is always at the highest setting regardless of where it was when the computer was shut down or where the slider in System--> Preferences--> Power Management is set at... It's easily corrected using the F6-F7 keys but it is a bit annoying...

---

### Post by bmach on 2010-06-13
Hi Everyone,

Ok. Looks like I managed to fix it which I'm stoked about. Probably not the most elegant solution but it worked for me so it might work for you all as well.

Run the following commands
```
cd /proc/acpi/video/VGA/LCD1
cat brightness
```

For me I get this:
```
levels:  0 10 20 30 40 50 60 70 80 90 100 
current: 70
```

This is basically saying that my LCD allows 0..100 brightness levels and the current is 70. For me personally, I want to set my brightness to 100 by default. For others that are experience other effects experiment with different levels to suit your needs. So to set my brightness to 100 I do this:

```
sudo bash 
  {Enter your password when prompted}
echo 100 > brightness 
```

For me this works and my screen goes brighter immediately after running the command. Yeah!

So now the trick is to put this into a script and have that script run automatically during my laptop boot process and prior to showing the login screen.

So I create a new script file to do this. Startup scripts are meant to go in the /etc/init.d/ directory so make sure you specify the path correctly:
```

sudo gedit /etc/init.d/set-preferred-brightness.sh
```

Add the line below into the file then save and close
```
echo 100 > /proc/acpi/video/VGA/LCD1/brightness
```

Now we have a script. Awesome. But we need to make it executable:

```
sudo chmod +x /etc/init.d/set-preferred-brightness.sh
```

Now all this has done is created a startup script and made it executable. But nothing is linking to the file to tell the system to actually run it at startup. To finish things off run this command:

```
sudo update-rc.d set-preferred-brightness.sh defaults
```

Now reboot your laptop and watch your brightness set to your required level (100 for me) and it will do it every time you boot. As I said at the start this probably isn't the greatest way to fix this (the whole update-rc.d seems wrong as it's not actually a service. But still it works in the end. If someone knows a better way please post!

---

### Post by bmach on 2011-06-20
Hey Everyone,

Anyone with a dv6, HP, or possibly even other laptops who have upgraded to Ubuntu 11.04 would have noticed that setting up the brightness on boot no longer works since the upgrade. This is because the command to change the brightness is different in 11.04.

To fix this, do the following

```
sudo gedit /etc/init.d/set-preferred-brightness.sh
```

And then paste the following into the contents over the top of the existing content

```

echo 10 > /sys/class/backlight/acpi_video0/brightness 

# Old command below no longer works since 11.04
# echo 100 > /proc/acpi/video/VGA/LCD1/brightness

```

Also note, if you want to adjust the brightness from the command line you will receive a permission denied error if you run this

```

sudo echo 10 > /sys/class/backlight/acpi_video0/brightness

```

The trick here is to use the tee command

```

echo 10 | sudo tee /sys/class/backlight/acpi_video0/brightness

```

---

### Post by hebetude on 2011-07-02
I have a dv6t quad ed (hybrid graphics).  Unfortunately this isn't working, there seems to be a problem with this laptop.  This appears to be the new control for brightness in 11.04,  but even modifying this value on boot to '3' I still boot with full brightness.

---

### Post by bmach on 2011-07-02
> **hebetude said:**
> I have a dv6t quad ed (hybrid graphics).  Unfortunately this isn't working, there seems to be a problem with this laptop.  This appears to be the new control for brightness in 11.04,  but even modifying this value on boot to '3' I still boot with full brightness.

How many directories are returned when you run "ls -l /sys/class/backlight/"

I have two returned in mine but when I adjust acpi_video1 nothing happens. So make sure you're working with acpi_video0. 

Also try doing things such as

```

cat /sys/class/backlight/acpi_video0/max_brightness 
cat /sys/class/backlight/acpi_video0/actual_brightness 

```

To confirm 3 is a valid value for your brightness.

---

### Post by hebetude on 2011-07-03
I've been hitting both, but it's interesting there are other files in there (not sure why I never checked).  I found max_brightness to be 10 so supposedly 3 would be 30%.

It's reporting actual_brightness as the value I set, even though its obviously at full brightness.  11.04/2.6.38-8-generic seems to be completely fubar around brightness.  Switching to discrete has the same problems.

---

### Post by hebetude on 2011-07-03
Ok interesting if this works: [http://askubuntu.com/questions/45153/is-there-an-alternative-to-redshift-and-f-lux-which-only-dims-the-screen/48952#48952](http://askubuntu.com/questions/45153/is-there-an-alternative-to-redshift-and-f-lux-which-only-dims-the-screen/48952#48952)

I removed the 'cut' part, as his command isnt distinguishing b/t disconnected and connected.  By doing this I can fade the screen, and it is superb.  I'm curious why xrandr can do it, but setting the /sys/ properties does not.

**sigh**

---

