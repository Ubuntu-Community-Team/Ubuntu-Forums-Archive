---
title: "Installed package and can not find it in software center"
date: 2012-07-04
forum: Hardware
---

### Post by Bradford1040 on 2012-07-04
> **joey89 said:**
> Hi,

I bought the R.A.T. 9 Mouse and got the most functions working on my Ubuntu 10.04LTS 64Bit.

I´m writing this thread because many people have problems with this mouse on Ubuntu and maybe we can fix the last problem i have with this mouse.

Here is how you get the most functions of the mouse working:

I found out that the Mode-Button on the mouse has access to the X-Server and disrupt it.
With the Command (in terminal) "xev | grep button" I found out that the Mode Button is registered as Button 13, 14 und 15 on my PC.
To get the mouse working i have deactivated this buttons in the Xmodmap.
Enter following command in the terminal "sudo gedit /etc/X11/Xmodmap". Usually this file is blank, so write the following text in it: "pointer = 1 2 3 4 5 6 7 8 9 10 11 12 0 0 0 0 0 0 0 0 0" and save the file. After restarting the X-Server (Logoff/Login) the mouse should work.

To use the thumbwheel and thumbbuttons i installed the program "imwheel" (from the Software-Center).

In the file startup.conf from imwheel i wrote:
[I]IMWHEEL_START=1
IMWHEEL_PARAMS='-b "0 0 0 0 8 9 10 11 12"'[/I]

And in the imwheelrc - file i wrote:
[I]".*"

#   Button 8 (Thumbbutton reverse)
None, Thumb1, Control_L|Alt_L|t

#   Button9 (Thumbbutton forward)
None, Thumb2, Alt_L|a

#   Button10 (Thumbwheel right)
None, ExtBt7, Control_L|Alt_L|Right

#   Button11 (Thumbwheel left)
None, ExtBt8, Control_L|Alt_L|Left

#   Button12 (red sniper Button)
None, ExtBt9, Alt_L|F4[/I]

So now i´m using the thumbwheel for changing desktops (i do have installed compizconfig), the sniper button for closing windows, and the other thumbbuttons for starting the terminal and my firefox internet browser.


The only function i have not yet got working is to adjust the DPI settings. The mouse can switch by herself the four DPI Settings (there are default setting on the mouse), so it works good.... but it would be nice to adjust the DPI´s.

Do you have any idea to fix that?

greetings, joey

OK a true dummy question? I installed this in software center and I can't find the dam thing lol, I have done everything but find anything relating to IMMOUSE so please help a fool! 

It is most likely right in front of me but I am new and don't see it. I am going to continue goggling but I think you and this site are about my best hope!

---

