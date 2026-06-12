---
title: "Ubuntu and Asus touchpad"
date: 2008-06-25
forum: Hardware
---

### Post by larbac2006 on 2008-06-25
Hello

I have a problem with my laptop touchpad. Every time I boot Ubuntu, I have to go to the console and run 2 commands to the scroll work:

sudo rmmod psmouse
and
 sudo modprobe psmouse rate=50 proto=imps

After this the scroll works again.
How can I activate automatically these commands at boot??

Thank You

---

### Post by lswb on 2008-06-25
cd /etc/modprobe.d

As root create a file (suggest using the name psmouse so you can locate it easily later, if necessary) with this line in it, or add it to one of the files that already exists in the /etc/modprobe.d directory:

options: psmouse rate=50 proto=imps

After you save the file, you can rmmod psmouse (using the command modprobe -r psmouse is preferable to using the rmmod command in most cases) and then modprobe psmouse. These options will now be automatically used whenever the psmouse module is loaded. 

The files in /etc/modprobe.d are used to configure various options and aliases that will be used to load modules.  You can check the man pages for modprobe and modprobe.conf for more info.

---

### Post by larbac2006 on 2008-06-29
Hello

I'm a newbie at this.
Can you do me an example of how to create this file, you talk about?

Thanks

---

### Post by lswb on 2008-06-29
There are several ways, here is one: open a terminal, type the command 

  gksudo gedit

Enter your password when prompted and the gedit text editor will start with superuser permissions.

type the text you want to save, then select file/save form the menu in the usual way. In the line for file name, type
   /etc/modprobe.d/psmouse
The "psmouse" part can be any file name but it must be in the /etc/modprobe.d diectory.

Then exit from gedit and the terminal.

Another way would be to open a terminal, then type these lines, pressing <ENTER>
after each and entering password when requested:

cd /etc/modprobe.d
sudo -s
echo "options: psmouse rate=50 proto=imps" >psmouse
exit
exit

Explanation: cd command changes to correct directory; sudo -s will start another shell as superuser after asking for your password. Then the echo command is redirecting it's output into the file psmouse, instead of just echoing it to the screen as it normally would. The first "exit" will exit from the superuser shell, and the second "exit" should close the terminal.

---

### Post by lswb on 2008-06-29
...

---

### Post by jonofan on 2008-06-30
Great, that fixes my problem. So after making the psmouse file, does this automatically run on startup? Or do I still need to type sudo modprobe psmouse?

Thanks

---

### Post by lswb on 2008-06-30
From what you posted earlier, it appears the psmouse module is loading automatically at boot, as expected, so you shouldn't need to do anything else. If for some reason the psmouse module is not loading automatically, you can add it to the file /etc/modules. This file is only writeable by root, so if you do need to edit it, use 
   gksudo gedit /etc/modules,  

add a line with the single word "psmouse" (without quotes) to the file , then save and exit

---

### Post by larbac2006 on 2008-07-07
HI

Sorry, but only today I coud test your solutions, but they didn't worked.
How can I know if the psmouse module is loaded at startup??

Thanks

---

### Post by lswb on 2008-07-07
> **larbac2006 said:**
> HI

Sorry, but only today I coud test your solutions, but they didn't worked.
How can I know if the psmouse module is loaded at startup??

Thanks

Do you mean you couldn't create the file, or that the mouse is not working?

To see if the module is loaded, in a terminal type

lsmod |grep psmouse

---

### Post by larbac2006 on 2008-07-12
Hi

I think the file it's created. When I execute the command you said, I get this:
 psmouse    40336  0

But the scroll continues not to work. I still have to do the rmmod psmouse and sudo modprobe psmouse...

This is weird..

Thanks for your help

---

### Post by larbac2006 on 2008-07-27
Hi

My problem still remains... Any other sugestion??


:(:(:(

---

### Post by lswb on 2008-07-27
Did you verify that the file in /etc/modprobe.d was created correctly? If so it should cause the options you wanted to be included whenever the psmouse module is loaded. If it still doesn't work, I'm out of ideas, except perhaps for adding the rmmod and modprobe lines to /etc/rc.local. I don't really like that idea, though, simply because the /etc/modprobe.d files are the documented method of configuring module loading options. On the other hand it wouldn't hurt to try it. Perhaps there is some kind of timing issue that prevents your touchpad from initialising until later than normal during boot.

---

### Post by aasami on 2010-11-13
The two-finger multitouch scrolling worked for me on ASUS K50IJ until upgraded to 10.10 Maverik Meerkat.

But it was just changes in default setting.
I reenabled it as 1-2-3 in
System > Preferences > Mouse > Touchpad > Scrolling > Two-finger scrolling

Now it works as before. :) Piece of cake.

---

### Post by Dale61 on 2010-11-14
There is a way to avoid the headache of not having your touchpad not work, and that is to do what I have done.

It's a USB mouse.  I use a Logitech M90, and it works flawlessly.

---

### Post by Zapata1879 on 2011-03-10
hi!

i had the same problem after having ubuntu upgraded to maverick. When i followed your instructions, i just left away the colons:

instead of options: psmouse rate=50 proto=imps, 
i wrote down: options psmouse rate=50 proto=imps 

and saved the file as psmouse.conf. For me it worked out that way. Hope it works for you either!

Cheers!

---

### Post by jelevin on 2011-03-20
> **Zapata1879 said:**
> hi!
 
i wrote down: options psmouse rate=50 proto=imps 

and saved the file as psmouse.conf. For me it worked out that way. Hope it works for you either!

Cheers!

This worked perfectly for me for my new ASUS A52F-XT22 Laptop Computer.

Should there be a tab in the gui mouse settings that recognizes the touchpad?  Is there anyway to get that?

Thanks

---

