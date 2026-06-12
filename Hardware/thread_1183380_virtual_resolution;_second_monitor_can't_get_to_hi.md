---
title: "virtual resolution; second monitor can't get to higher resolution"
date: 2009-06-10
forum: Hardware
---

### Post by wkck on 2009-06-10
Hi everyone!  I have an issue with my second monitor's resolution.  I have a Dell laptop, and a Samsung external monitor running through the dock to my laptop.  My goal is to have the Samsung monitor to be on at 1280×1024, and the laptop screen to be off.  

Just earlier today I was able to get this by using a combination in "Display Preferences" and restarting.  But since, I redocked my laptop and (thinking it may save me time of rebooting) I followed the prompt about the "virtual resolution" and logging out and back in.  Now, no matter what I try, I can only get the laptop screen off, and the Samsung on at 1024×768.  Before there was a drop down menu for the Samsung's resolution and when I would restart it would show 1280x1024, now I cannot see that option.

Any ideas?  Thanks so much for your help!

---

### Post by wkck on 2009-06-10
I solved the problem by using using parts from another thread.  

1) I entered into the terminal:  sudo gedit /etc/X11/xorg.conf

2) Then on the screen that came up I entered the red part in the text below:

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	1024 1536
		[COLOR="Red"]Virtual 1280 1024[/COLOR]
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

3) Then I hit save on that window.  Then restarted.  And the higher resolution was there for my to select in System > Properties > Display

---

