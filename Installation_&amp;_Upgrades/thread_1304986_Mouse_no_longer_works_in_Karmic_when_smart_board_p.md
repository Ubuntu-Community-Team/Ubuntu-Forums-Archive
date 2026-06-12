---
title: "Mouse no longer works in Karmic when smart board plugged in"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by cayhorstmann on 2009-10-29
I am running Karmic and plug in a Smart Tech smart board. It messes up my mouse (it now keeps getting pulled to the northwest corner whenever I try to move it), and I get occasional kernel null pointer errors. The Smartboard pen works fine as a mouse.

dmesg contains this:

[ 5114.216700] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 5115.416042] usb 6-2: new full speed USB device using uhci_hcd and address 5
[ 5115.601158] usb 6-2: configuration #1 chosen from 1 choice
[ 5115.612123] input: SMART Technologies Inc. SMART Interactive Whiteboard Controller (SB6) as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input22
[ 5115.612267] generic-usb 0003:0B8C:0001.0007: input,hiddev96,hidraw0: USB HID v1.11 Mouse [SMART Technologies Inc. SMART Interactive Whiteboard Controller (SB6)] on usb-0000:00:1d.0-2/input0

This used to work fine on Hardy and Intrepid. 

How can I troubleshoot this? Is there some way of tweaking or blacklisting something? It's the first time I had a failure with the mouse.

Thanks,

Cay

---

### Post by aeball1053 on 2009-11-04
I have the same problem and have been in contact with smart and they suggested do a firmware update. I havent tried it yet but will keep you posted.

---

### Post by jork on 2009-11-13
Same problem here, using a SmartBoard 680. This worked fine with Jaunty

---

### Post by crocuta on 2009-11-18
I'm in the same case, still have not updated the firmware yet.
If you connect the smart board with the computer on, the mouse pointer keeps jumping to the upper left corner.

If you connect the smart board while the computer is off, the mouse pointer will keep jumping to the center of the screen.

I was hoping my problem with ubuntu-smartboard would be fixed somehow in karmic: i need the digital markers to work over fullscreen OpenOffice.org presentations.    It used to work with ubuntu 8.04, but some update broke this.

But, alas, as of now the situation is worst :(

---

### Post by Onesimus on 2009-12-01
Has anyone found any solutions to do this ?

I was wondering whether it might not be the mouse that is causing the problems, but actually the touchpad of the laptop.  Is anyone having problems with Desktops ?  

My reasoning that it may be the touchpad is that the interactive nature of the Smartboard is like one v. large external touchpad.  Consequently, when the smartboard is plugged in, it now has two touchpads that are providing conflicting information.

I haven't been able to diagnose any further, partly because it's my wife's laptop and the smartboard is at her school.

Any info would be appreciated.

---

### Post by crocuta on 2009-12-01
I have not found any solution to this problem.  In my school it happens with 4 desktops and one laptop.

---

### Post by Onesimus on 2009-12-01
> **crocuta said:**
> I have not found any solution to this problem.  In my school it happens with 4 desktops and one laptop.

Have you updated the firmware yet ?  Presumably, if you have then it didn't make any difference.

---

### Post by jork on 2009-12-01
> **Onesimus said:**
> Have you updated the firmware yet ?  Presumably, if you have then it didn't make any difference.

I did a firmware update (with a Windows machine), but this didn't solve the problem. :(

---

### Post by Ductaman on 2009-12-10
Yeah, same problem here.

---

### Post by mtoddedwads on 2009-12-12
I have the same trouble as you all.  I'm running Ubuntu 9.10 with an Lenovo X41 Tablet PC.  Is it possible to write a script to disable the onboard mouse and/or touchscreen when the smartboard is plugged in?

I would assume so, but sadly I don't know how to do this.  Does this sound like a possibility to you all?  If so, I'll begin investigating how to do it.

---

### Post by mtoddedwads on 2009-12-13
The following script toggles the trackpoint "eraserhead mouse" off or on depending on its current status.  I'm thinking that running the script before plugging in the smartboard may help, since it will eliminate competition between the smartboard and the trackpoint.

#!/bin/bash
X="$(lsmod | grep psmouse)"
if [ -n "$X" ]; then
modprobe -r psmouse
exit
fi
modprobe psmouse

I'll test this out later today once I get a chance to visit my classroom (I have no smartboard at home).  Recall that I'm using Ubuntu 9.10 with an X41 IBM/Lenovo Thinkpad.

---

### Post by mtoddedwads on 2009-12-14
Okay.  I tried my script earlier today.  The script works well in terms of disabling my computer's trackpoint mouse.  However, when I plug the smartboard usb cable in, the mouse cursor still moves to the upper left-hand corner of the screen.

I'll continue messing around with this.

---

### Post by mtoddedwads on 2009-12-15
Hello Todd,

Thank you for contacting SMART Technologies.

I understand that you are having issues with your SMART Board™ interactive whiteboard while using the Ubuntu operating system.

We know of the issue and know the answer to the issue:

Create a file under /etc/hal/fdi/policy/ entitled 10-smarttech.fdi with the contents as follows:

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.category" contains="input">
      <match key="info.product" contains_outof="SMART">
          <merge key="input.x11_driver" type="string">evdev</merge>
          <merge key="input.x11_options.SendCoreEvents" type="string">false</merge>
      </match>
    </match>
  </device>
</deviceinfo>

Then plug in the SMART board and start the SMART Board Service manually.          
           
If you have any further questions or concerns, please contact us again.

SMART Technologies 
Colin Conrad 
Technical Support 
Phone: 1.888.427.6278
Phone (International): 1.403.245.0333
Fax: 1.403.806.1256
Mail to: [email]info@smarttech.com[/email]
Web: [www.smarttech.com](www.smarttech.com)

---

### Post by Albertoc67 on 2010-02-26
Hello to everybody,
I also had these problems:

[FONT=Arial][SIZE=2]1) the arrow pointer remains in the upper left corner of the board like [FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT]it was retained by a spring.[/SIZE][/FONT] 
[FONT=Arial][SIZE=2]2) the commands are received by the Smart Board 2 inches up your finger [FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT]or Smart Board coloured pen.[/SIZE][/FONT] 
 
[FONT=Arial][SIZE=2]The technician did a lot of tries and it seem that the first problem has [/SIZE][/FONT]
[FONT=Arial][SIZE=2]solved changing to Ubuntu 9.04 and installing the older version of your [/SIZE][/FONT]
[FONT=Arial][SIZE=2]notebook installation files.[/SIZE][/FONT] 

[FONT=Arial][SIZE=2]Now we still have the second problem.[/SIZE][/FONT] 
[FONT=Arial][SIZE=2]If you have the solution, please mail me what we must do.[/SIZE][/FONT] 
 
Does anybody of you solve these problems?
 
Many thanks (from Italy)

---

### Post by crocuta on 2010-02-26
Hi Alberto

The solution given by mtoddedwads worked excelent on my computers and it's quick to setup.   Whenever i get a new computer to set up I install 9.10, the latest Notebook (this installation comes with the drivers)  and then copy the file    10-smarttech.fdi   to /etc/hal/fdi/policy/    Remember, you create this file with the contents proposed by mtoddedwads early in this thread.

Then it works fine,  with the tools and smartboard service starting automatically  wether you start the computer with the board connected or not.



Regarding the second problem, i think the difference between the place where you touch the board and the place where the mouse pointer goes is equal to the height of the taskbar. So far, we have been orienting or calibrating  slightly off the crosshairs, in the space between the upper edge of the red cross and the upper vertex of the diamond.   

I have attached a pdf with a drawing we made about this for the teachers.


All this also solved a very annoying problem we have been suffering (really!). Starting with Ubuntu 8.04, the ink overlay stopped working with OpenOffice Impress presentations.  Actually, the ink layer did appear whenever you picked up any physical marker,  but instead of coming on top of everything else  it appeared below the slide.  We had to  ALT-TAB to bring the ink layer to the foreground and it was very poor solution because the teacher had to go to the keyboard to do that.      
We worked with the smart tech support guys  and they could replicate the problem, but didn't find a solution.    With the "10-smarttech.fdi" procedure, the smart tech support guys finally addressed the problem.



Hola dal Messico

---

### Post by bbehrendt on 2010-05-17
The fix stated above works for 9.10 but not for 10.04.  I have submitted a bug report to them.  Hopefully they will get this working soon.

-bj

---

### Post by bbehrendt on 2010-05-21
Just got a message back from Smart. The only way to get it to work in 10.04 as of now is to recompile a kernel.  

Hi BJ,

Thank you for your response.
 
I have consulted with the product specialist again about this issue. I have provided a possible fix below.
 
NOTE: SMART does not officially support Ubuntu 10.04.
 
NOTE: The actions in this script may void any commercial support which you may have purchased.
 
NOTE: This should only be attempted by a qualified system administrator.
 
When connecting a SMART interactive product on a Linux distribution with kernel
2.6.30 or greater, the mouse cursor will always jump to the top left corner of the display. These instructions will fix that issue.
 
These instructions do not apply to a particular Linux distribution. But it is only intended for Linux kernel 2.6.30 or greater. You will need to do this every time your distribution releases a kernel update. This method provides you with drivers that are closer to what your system is currently running.
 
1. Download the source code for the Linux kernel. Every distribution does this differently. Consult your distribution's website for details.
 
2. Edit linux/drivers/hid/hid-input.c. In the function
   hidinput_configure_usage() search for:
 
            case HID_UP_DIGITIZER:
                        switch (usage->hid & 0xff) {
 
   Add this code immediately after the switch statement:
 
                                    case 0x00: /* Undefined */
                                                goto ignore;
 
3. Save the file.
 
4. Build and install your kernel according to your distributions instructions.

If you have any further questions or concerns, please contact us again.

---

### Post by Onesimus on 2010-08-19
Is there any further progress on this - have others been able to get it to work in 10.04 ?

I don't know how (or particularly want) to recompile the kernel.

@bbehrendt
What version of smartboard were you using ?

---

### Post by crocuta on 2010-08-19
I don't remember where i got this fix, but it helped with Ubuntu 10.04.  Credit to whoever figured it out:

Make a script with these contents:

```
#!/bin/bash
sudo rename /etc/udev/rules.d/60-SMARTBoard24.rules /etc/udev/rules.d/60-SMARTBoard24.old &&
sudo cp 60-SMARTBoard32.rules /etc/udev/rules.d/ &&
sudo udevadm control --reload-rules
```


Also create the file 60-SMARTBoard24.rules that contains this:

```
#SMART Technologies rules for permissions.
KERNEL=="ttyS*", MODE="0666"
SUBSYSTEM=="usb", ATTR{idVendor}=="0b8c", MODE="0666"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_interface", ATTR{idVendor}=="0b8c", MODE="0666"
SUBSYSTEMS=="usb", DRIVERS=="usb", ATTRS{idVendor}=="0b8c", MODE:="0666"
#
#Kernel 2.6.32 and greater has a bug that causes the mouse pointer to jump to the top left corner in HID mouse mode.
#Disable the event stream for affected products.
#Actually the bug began in 2.6.30, but these rules only work on 2.6.32.  You need an fdi policy file to work around 2.6.31.
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0001", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0002", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0003", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0004", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0005", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0006", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0007", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0008", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="000a", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="000b", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0017", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0060", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0061", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0042", NAME="SB%k"

```

Reboot.
Regarding the vertical offset of the pen and the effect on screen, i think it has something to do with the system taskbar because is about the same size.    What we do for now is aim a little higher on the crosshairs when orienting.

---

### Post by Onesimus on 2010-08-19
@crocuta
Many thanks for a quick reply.

A quick summary of what I have done (this was prior to my previous post):  I downloaded the latest version of the Smart software + drivers package (10.2.321.0) - this caused mouse to go to top left corner.  I then updated my drivers file to 10.2.100.0 (it was something like 10.2.97.0 before the update) - required a download of 76Mb.  I haven't yet checked whether this has solved the issue as I am now at home.

However, looking at my current files in the rules.d directory in conjunction with your posting.  I don't have the file 60-SMARTBoard24.rules, but only 60-SMARTBoard32.rules.  This is a replica of what you gave in your post (i.e. 60-SMARTBoard24.rules).  I am assuming (in your post) that it should have had the name 60-SMARTBoard32.rules, otherwise the script wouldn't work.

I will let you know whether updating the drivers has fixed the issue (which seems to be the same as your suggestion)

---

### Post by mrtumtum on 2010-12-02
Problem seen on upgrade to new kernel. the fix is in:
[http://ubuntuforums.org/showthread.php?p=9336975](http://ubuntuforums.org/showthread.php?p=9336975)
crocuta's answers works:

For someone mot familiar with the command line do this:
$ sudo -s

this command sets the command line to su mode
you will be prompted for a su passwd
#
# cd /etc/udev/rules.d

cd changes the working directory, it's a good idea to type only the first few letters of directories and files within directories and use the tab key, which will auto complete
the directory and/or filename, beware will work under bash command line interpreter

#ls : to find the name of the file 60-SMART24....

ls tells the command line interprter to list the files in a directory
#cp 60-SMARTBoard24.rules 60-old.rules


you have now made a copy of the original file 60-SMARTBoard24.rules and named it 60-old.rules.

#gedit /etc/udev/rules.d/60-SMARTBoard24.rules

opens a text editor
first  delete the current contents and paste the following:

#SMART Technologies rules for permissions.
KERNEL=="ttyS*", MODE="0666"
SUBSYSTEM=="usb", ATTR{idVendor}=="0b8c", MODE="0666"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_interface", ATTR{idVendor}=="0b8c", MODE="0666"
SUBSYSTEMS=="usb", DRIVERS=="usb", ATTRS{idVendor}=="0b8c", MODE:="0666"
#
#Kernel 2.6.32 and greater has a bug that causes the mouse pointer to jump to the top left corner in HID mouse mode.
#Disable the event stream for affected products.
#Actually the bug began in 2.6.30, but these rules only work on 2.6.32.  You need an fdi policy file to work around 2.6.31.
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0001", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0002", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0003", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0004", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0005", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0006", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0007", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0008", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="000a", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="000b", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0017", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0060", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0061", NAME="SB%k"
KERNEL=="event*", ATTRS{idVendor}=="0b8c", ATTRS{idProduct}=="0042", NAME="SB%k"


save the file


#less 60-SMARTBoard24.rules

this is to make sure the new setting are in place.

reboot your computer

re-v

[EMAIL="mrmrmr50@rediff.com"]mrmrmr50@rediff.com[/EMAIL]

---

