---
title: "Two exact same monitors have different resolutions"
date: 2019-05-17
forum: Hardware
---

### Post by West Swan on 2019-05-17
[SIZE=2]Hello,

I have an HP Pavilion a6040a tower running Lubuntu 16.04

I have ordered a GT710 graphics card with the intention of using it to extend the display (dual monitors).  This should arrive Monday or Tuesday.

Currently using the onboard graphics (VGA).


Today I purchased two monitors Viewsonic VX2235WM which have a native resolution of 1680 x 1050

Testing both of them.  One monitor lets call it the "Good One" is perfect.  The other monitor lets call it the "Bad One" has resolution of 1024 x 768 so everything on the screen is too big.

Under Display settings it only allows  1024 x 768  resolution or 800 x 600  or 848 x 480  or  640 x 480  for this one.


I plugged this same monitor into a different computer running Windows 10.  It initially came in with the same resolution of 1024 x 768 but then going into display settings it let me change it to the correct resolution which persists with restarts etc so all good there.  

In Lubuntu I have already installed ARandR in preparation for when the graphics card arrives so I can more easily extend the display.


With regards to the "Bad" monitor should I attempt to get it at 1680 x 1050 now or wait for the new graphics card to arrive?  

It seems strange that two monitors the exact same part number would have different resolutions like this.


My computer knowledge and skill set  are with Windows computers however I can follow instructions to get things done.  

Just like a recipe.  Do step 1 then step 2 then step 3 etc and before you know it lo and behold you have a croquembouche   :p 


Please let me know if more information is required.


Regards,

Paul
[/SIZE]

---

### Post by Autodave on 2019-05-17
How are the monitors connected to the PC: what kind of cable?

---

### Post by West Swan on 2019-05-17
Hi Autodave,

Currently VGA cable from tower to monitor.

In ARandR shows up as VGA1

When new graphics card arrives one will be attached via DVI-D and the other via VGA.  The card has a HDMI port as well but I don't have an adapter and the monitors only have DVI and VGA.


Regards,

Paul

---

### Post by West Swan on 2019-05-17
I might not have been completely clear.

I tested one monitor with the one VGA connection shut down the computer then put that monitor in another room

Then I connected the "Bad" monitor to the computer and switched the computer on and got the low resolution.

So only one monitor was connected to the computer at any one time.  I won't be connecting both monitors simultaneously until the new graphics card arrives.

---

### Post by DuckHook on 2019-05-17
The "bad" monitor may not be reporting proper EDID information. Even though models are supposedlly identical, OEMs may source parts from different suppliers.

Since you know that the "bad" monitor is, in fact, capable of 1680x1050, do the following (with the "bad" monitor plugged in):

[list=1]
[*]Generate a file with the results of CVT:```
cvt 1680 1050 60 > ~/Desktop/cvt_results
```
[*]It will look something like the following, but will vary slightly. The important part is the stuff after "Modeline":```
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```
[*]Then, taking care to use the info in your CVT output to **replace the example code below**:```
xrandr --newmode "1680x1050" 146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```
[*]Then:```
xrandr --addmode VGA1 1680x1050
```
[*]Then:```
xrandr --output VGA1 --mode 1680x1050
```
[/list]
Note: Once your new card arrives, you will have to do this all over again.

To make the changes permanent (so that they survive reboot), put the above lines in ~/.xprofile (if it doesn't exist, create one), taking care to again replace my example code with your real info:```
#!/bin/bash
xrandr --newmode "1680x1050" 146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
xrandr --addmode VGA1 1680x1050
xrandr --output VGA1 --mode 1680x1050
```

---

### Post by rbmorse on 2019-05-17
It's quite likely that the EDID module in the "bad" display has failed, or the EPROM that holds EDID data got scrambled.  I used to see this a lot when I was fooling with hardware for a living.  DuckHook should get you going.

---

### Post by West Swan on 2019-05-17
Hi DuckHook,

Thank you for that.

I am actually already confused though ;)


When you say to do this:

Generate a file with the results of CVT: 	
Code:

 	cvt 1680 1050 60 > ~/Desktop/cvt_results

Do you mean I should go into LXTerminal and type in    cvt 1680 1050 60 > ~/Desktop/cvt_results

I don't think that is what you mean because when I do that and hit enter nothing happens that I can see.



 



Sorry as you can see I am not that terminal literate.   I can do simple stuff like sudo apt-get install libreoffice  but that is about it.


I actually have to head off now.  Getting up at 4.30 am tomorrow for the elections here in Australia.

Thanks again,

Paul

---

### Post by DuckHook on 2019-05-17
> **West Swan said:**
> …When you say to do this:

> Generate a file with the results of CVT: 	
```
cvt 1680 1050 60 > ~/Desktop/cvt_results
```

Do you mean I should go into LXTerminal and type in    cvt 1680 1050 60 > ~/Desktop/cvt_results
Yes
> I don't think that is what you mean because when I do that and hit enter nothing happens that I can see.
I was trying to make things easier and unintentionally confused you.

This should generate a file on your desktop containing the proper code as its content. The file will be called [FONT=Fixedsys]cvt_results[/FONT] and you can open it with any text editor.
> Sorry as you can see I am not that terminal literate…
No need for apologies. We all started out where you now are.
> I actually have to head off now…
No problem. Get back to it when convenient.

Just a note that I do delete thread subscriptions after 4 days of inactivity.

---

### Post by West Swan on 2019-05-17
Hi DuckHook,

Ah got it.

Ok.  All your information is the  same as mine with the exception that the results of the CVT in step 1  includes the refresh rate of 60.00
```
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```


This is not important though right as when I include it in Step 3 it seems to do nothing (step 4 gets the message xrandr: cannot find mode "1680 x 1050")

However as all your information was exactly the same as mine I just ignored the bit about the refresh rate and typed in step 3 exactly as yours above and whola steps 4 and 5 then worked 
and the resolution changed to 1680 x 1050 :-)


I wasn't sure whether or not to make this permanent as the new card will be arriving Monday or Tuesday and I didn't want to muck anything up.
So I just restarted and as you mentioned what I had done up till that point all went away and the 1024 x 768 came back.

Can I make the changes permanent now or should I wait?

With regards to ~/.xprofile is there a preferred way to create this and how do I save it etc?  Or does that code you give starting with #!/bin/bash actually create the profile?   


So yes it all looks to be going well.

Regards,

Paul

---

### Post by DuckHook on 2019-05-17
Please stay with standard fonts and formatting for the sake of readability. We have many users who use small screens (phones) or have vision challenges. Also, please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

I have edited your post to bring it into conformity with these posting guidelines. ;)

As to your questions:

[LIST]
[*]Considering that your card will arrive momentarily, you may wish to wait. The CVT output sometimes varies depending on your card, as does the actual mode (eg. VGA1 or VGA-1 or VGA-0)
[*]There is no preferred way to create *.xprofile*. It just needs to be a simple text file. I use the command line and *Nano*, but that's only because those are the tools I am most comfortable using. You can create it with leafpad. What's important is the content.
[*]Note: *.xprofile* must be in your home directory. Accuracy is important. You probably can tell by now that Linux is very sensitive to case, punctuation, typos, etc. Be sure to include the preceding dot in *.xprofile*, else it won't work.
[*]**#!/bin/bash** is called a shebang and must be the first line in *.xprofile*. It tells the system to execute what follows by interpreting it as instructions using bash.
[/LIST]

---

### Post by West Swan on 2019-05-17
Thank you - I will let you know when new card arrives and I've managed to get it all working .

---

### Post by West Swan on 2019-05-18
Hi DuckHook,

Should I create a new thread when I attempt to setup the dual monitors or just keep adding to this one?


Also I am confused about the .xprofile and how to create it.  I wish there was a simple graphical way of doing it :D   


Is this correct:

1.  Open up Leafpad;

2.  Paste the information starting with **#!/bin/bash** see below  (but with my specific information) into Leafpad; 

3.  Save this text document as **.xprofile**  or  **~/.xprofile**   (I'm not sure what to name it here.  Do I include the swirly line and the forward slash)?

4.  The location to save it is in the directory  **/home** which is in the** filesystem **directory.  Do not save it in the **Home Folder** which contains all the Pictures, Documents etc;

5.  Restart the computer and enjoy the correct resolution.



Here I am just testing your instructions to correctly highlight the output and click the #  button.  Did it work?

```
#!/bin/bash
xrandr --newmode "1680x1050" 146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
xrandr --addmode VGA1 1680x1050
xrandr --output VGA1 --mode 1680x1050
```

---

### Post by DuckHook on 2019-05-18
[LIST=1]
[*]The naming convention in Linux is: ~ stands for your home directory. Therefore, when used in instructions such as those given above, it refers to your personal home directory. The file name is just .xprofile (no ~ or /).
[*]You want the file to be put into the directory that contains your Documents, Downloads, Pictures (etc) directories. That is, in fact, your personal home directory (~). The general home directory—that is to say, /home is one further level up and is meant to contain all of the users permitted on your machine (you could just be one user among many). Do not place .xprofile there. It will not work at that level.
[*]To make sure that you are putting .xprofile into the proper directory, turn on "hidden files" in your file manager (you are probably using PCManFM) and look for a file called .bashrc. If that file exists, then you are in the right directory.
[*]Your use of [noparse]```
 and 
```[/noparse] tags works.
[/LIST]

---

### Post by DuckHook on 2019-05-18
A further note:

Your new card may not call the output mode VGA1. You must check to see what your new card actually labels this mode. Use arandr like you did before to determine this mode.

Also, you mentioned that your new card will output one stream as HDMI and the other as VGA. Therefore, you must be careful to match the proper mode to your "bad" monitor (the good monitor will likely be detected properly and automatically be configured optimally).

---

### Post by West Swan on 2019-05-18
Got it thank you :P

---

