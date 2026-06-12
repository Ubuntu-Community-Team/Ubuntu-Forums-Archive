---
title: "HOW TO: 3 Steps to Making your Touchpad play nice in Ubuntu 10.10"
date: 2011-03-04
forum: Hardware
---

### Post by unc0nn3ct3d on 2011-03-04
I created a little how to on my blog today at: [http://blog.netflowdevelopments.com/2011/03/04/getting-your-touchpad-to-behave-nice-in-ubuntu-10-10/]("http://blog.netflowdevelopments.com/2011/03/04/getting-your-touchpad-to-behave-nice-in-ubuntu-10-10/") and wanted to share with the community.  Pasted it below and clearly I'm using 'the right way' tongue and cheek so I don't wanna catch any flak for that y'hear? :)


Alright so easily one of the most frustrating things about having a laptop is the god damn touch pad.  Either it's jumping all over the place while you are typing, or misinterpreting a middle click and pasting junk everywhere or any number of other frustrating things it can do to make your life miserable.  Lucky for us Ubuntu allows you to dig around and reconfigure just about every aspect of the way it interacts with your hardware, touchpad included.

So today I sat down and put in the time to finally get my touch pad working the way I want it to work and this is what I came up with:

[SIZE="3"]**1.) Enabling 2 finger scrolling(the right way)**[/SIZE]

There are a few ways to handle this.  On the Ubuntu wiki they suggest that you Install the DKMS driver package provided in [https://bugs.launchpad.net/bugs/308191](https://bugs.launchpad.net/bugs/308191) (comment #115, #116). Reboot, and go to System > Preferences > Mouse > Touchpad and select "Two-finger scrolling".

But to be honest this just isn't precise enough for me and I feel much more comfortable editing system files than going through the GUI so this is how I take care of that:

    * Create a file in /etc/init.d and paste the following in:
[B]
    #!/bin/bash
    synclient VertTwoFingerScroll=1
    synclient HorizTwoFingerScroll=0
    synclient EmulateTwoFingerMinW=5
    synclient EmulateTwoFingerMinZ=48[/B]

It should be pretty self-explanatory what those values mean.  The only thing left to do with this is to make this program start at boot time.  You need to chmod this program to 755 or r+x and then you can go into system->preferences->startup applications and add it or type update-rc.d FILENAME defaults , obviously replacing FILENAME with whatever you called it.

**[SIZE="3"]2.) Automatically disabling the touchpad while typing(The right way)[/SIZE]**

So again you can go into system/prefs/mouse and set this to off, but once again it's a limited shitty way to accomplish what you want accomplished here.  There is a little program called syndaemon that controls this sort of thing and it will allow you to fine tune it a lot more.  The main problem with doing it through the gui is that you can't control the delay that occurs between finishing typing and when the touchpad is activated again.  By default it is .5 seconds or aruond there which is way to short and will result in the touch pad coming back to life and wreaking havoc on you after the smallest pause in typing.  We want this to be between 1-2 seconds and so for that we can create the following little script, again placing it in /etc/init.d that contains the following:

[B]    #!/bin/bash

    syndaemon -i 2 -d[/B]

If you want to adjust that delay time just change the 2 to something smaller or larger, whatever suits your needs.  Follow the rest of the instructions above to make it a startup script and you are good to go

**[SIZE="3"]3.) Create a shortcut toggle to disable/enable your touchpad completely.[/SIZE]**

Now all of the above stuff is great but to be honest even then it doesn't get the touchpad out of the way 100% of the time while you are typing and especially if you have a usb mouse plugged in you probably want to just turn the whole damned thing off to save yourself the headache.  But if the headache of turning it on and off is greater than it is causing in the first place then what's the point right?  Well I did a little bit of simple bash scripting today and came up with the following script that will allow you to toggle the damned thing at the touch of a button.

If you don't have a ~/.local/bin directory now then go ahead and make one, it's a real handy place to have for custom scripts.  You are also going to have to add that path to your environment, I do that by simply putting the following in my ~/.bashrc:
[B]
    PATH="$HOME/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"[/B]

Before we can properly make our script we need to find the ID number for your touchpad.  You do this by typing xinput -list in shell and looking for the touchpad.   It should have an ID= next to it with your ID number.  My touchpad is device #14 so I use 14 in the script below but if yours is different you will need to change that number to correspond with your touchpad's ID.

Inside your ~/.local/bin/ directory you are going to create a file, I call mine toggle_touchpad and insert the following code:

[B]   #!/bin/bash

idNum=$(xinput -list | awk /Synaptics/ | grep -o "id=.." | sed 's/id=//')
state=$(/usr/bin/xinput -list $idNum | grep "disabled")

if [[ $state ]]
then
/usr/bin/xinput set-prop $idNum "Device Enabled" 1
else
/usr/bin/xinput set-prop $idNum "Device Enabled" 0
fi

[/B]
This guy just looks up the state of your touchpad, greps it for the word disabled and if it finds that word it assumed the touchpad is off and turns it on, if it doesn't find that word it assumes the touchpad is on and turns it off.  Easy Peasy.  Now just go to system -->Preferences --> Keyboard Shortcuts and create a shortcut for that command and you're done.

Now, finally your touchpad nightmares should be over and you can live a laptop life without fear and dread of it destroying data, pasting garbage everywhere or moving your cursor where it doesn't belong.

Huzzah!

---

### Post by unc0nn3ct3d on 2011-03-06
I had to update the last script in there that toggled the touchpad on and off.  I realized that if I booted my machine with my usb mouse plugged in the ID numbers would be different which can result you shutting down some pretty important devices(like the keyboard) without which it's impossible to turn it back on again.
So now the script goes out and finds which device your touchpad is first and makes sure it's using the right ID number.

---

