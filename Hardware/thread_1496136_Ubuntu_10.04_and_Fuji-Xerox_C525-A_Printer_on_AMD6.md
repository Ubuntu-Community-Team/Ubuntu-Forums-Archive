---
title: "Ubuntu 10.04 and Fuji-Xerox C525-A Printer on AMD64"
date: 2010-05-28
forum: Hardware
---

### Post by Plane Jane on 2010-05-28
Hi All,

I struggled to get my Fuji-Xerox C525-A printer working on my Ubuntu 10.04 AMD64 system. I got it working and wanted to post to the forums in case other people were struggling to get their printers working. I might add that Fuji-Xerox Australia were completely unhelpful in this process and when this printer dies, I'll go elsewhere as a result.

Trawling the net shows a lot of people having the same problem, a dead printer! There are a few solutions, none of which worked for me. When I tried converting using Alien, because the only rpms you can source on the net are for 32-bit systems, the conversion failed. I'm not a linux guru and had no idea how to make Alien produce a 64-bit .deb file so I played around and finally got a result for myself via some manual copying of files.

Here's how I did it:

**Make sure your printer is connected and turned on before you start this process!!!**

First, I downloaded the tar file from [http://www.fujixeroxprinters.com/](http://www.fujixeroxprinters.com/) because I am in Australia, I went to the Australian-specific site. :)

Using the above logic, I clicked Support > Drivers > Product > C525A

I then selected Linux and English from the drop downs. For some reason, I am presented with Windows/Mac drivers and also, other languages. If you scroll down, you will eventually see:

[INDENT]Driver
Linux Print Driver
dpc525a_linux_.0.0.tar.zip[/INDENT]

Hit the download button and save this file somewhere you will know where to find it later. I chose my user's home Download directory.

Once the file downloaded, I opened up Nautilus as root. This is really important because if you don't do all of the following as root, you get permissions problems when you copy the files over. Open a terminal and type:

```

**gksudo nautilus** 

```

This is the command I used, maybe there is a better command, but this works for me :)! This is also the only command-line input you have to use. I'm not very command-line orientated and prefer GUI goodness, so the rest of this process is point and click from now on.

Enter the root password and to make it even easier for yourself, you can split nautilus into two panes. You do that by pressing F3 when Nautilus opens, or via: View > Extra Pane. We can't do this in Windows so if you are a bit puzzled, [here is a screenshot of nautilus with two panes]("http://www.flickr.com/photos/plane_jane/4648464021/sizes/l/"). 

Now, on the left pane, I created a Downloads directory. On the right pane, I navigated to where I saved the driver tar file and copied into the download folder I just created for root. Simply drag and drop from one pane to the other. We will be doing this a lot from now on!

I then un-compressed the file. Double clicking the tar file opens File Roller and its easy enough to extract the file here. Then quit File Roller.

You now have the extracted files in a new directory, mine was called C525A_LinuxE. When we go into this new directory, I can see Fuji_Xerox-DocuPrint_C525_A_AP-1.0-1.i386.rpm. This is the file that Alien won't convert to a deb for me! :(  [COLOR="Red"]*If a Ubuntu-Guru is reading this and knows how to convert this 32-bit rpm into an AMD64 .deb file, please tell me how by making a comment. It might be handy for me in the future.*[/COLOR]

When I click this .rpm file, File Roller launches again for me. I extract these files and another new directory is created for me. You will see a **usr** directory appear thanks to File Roller. If you explore this usr directory, you will see that there are two other directories which contain a whole bunch of other directories and files within them. What this does is actually show me where the various bits and pieces of the driver files need to be copied into the directory structure of my system.

FTR, these file-system locations are:
 
[INDENT][B]/usr/lib/cups/filter and,
/usr/share/cups[/B][/INDENT]

So, first things first, I leave the left pane of Nautilus alone, and in the right pane, I navigate to /usr/lib/cups/filter. I copied all of the files from /root/download/C525A_LinuxE/usr/lib/cups/filter into the right pane. Dragging and dropping has never been so much fun right? :P

I copied **ALL** of these files, but, the really important file for Ubuntu is **FXM_PF**. If you are like me, you will just right click on PXM_PF and double check its file permissions are set to root. :)

Next, I use the left pane and navigate backwards to the /root/download/C525A_LinuxE/usr/share/cups directory. On the right pane, I go to the /usr/share/cups directory on my file-system. I again drag and drop from left pane into the right pane, the entire **[COLOR="Red"]FujiXerox[/COLOR]** and the **[COLOR="Red"]model[/COLOR]** directories.

With all of this copying of files into their correct and appropriate locations on my file system, I now exit nautilus and just open up the Gnome printer setup dialogue at:

[INDENT][COLOR="Red"]System > Administration > Printing[/COLOR] and work through the Ubuntu printer setup wizard.[/INDENT]

You did connect and turn on your printer like I suggested earlier didn't you??? If you did, your Fuji-Xerox C525A might be "found" for you automagically by Ubuntu's brilliance. It still needs to be told how to work by Ubuntu anyway.

Now that all the files are in their correct places in our filesystem, it's a simple process to hit the add button and work through the Ubuntu Gnome Printer installation routine. These steps are:

[LIST=1]
[*][COLOR="SeaGreen"]Add > FujiXerox Docuprint C525 A AP, hit forward button[/COLOR]. It goes online and searches for drivers that don't exist thanks to Fuji-Xerox's stinginess. Once it can't find an online driver, we get the Choose Driver window.


[*][COLOR="SeaGreen"]Select the "Provide PPD file" option and navigate via the drop down file finder to: /usr/share/cups/model/FujiXerox/en where you should see the FX_Docuprint_C525_A_AP.ppd driver file and pick open[/COLOR]. You should see the PPD file displayed and you can now hit the forward button.


[*][COLOR="SeaGreen"]I just hit the forward button all the way from here and allowed the default options to be setup for me, until I got to apply[/COLOR]. I took advantage of the offer to print a test page.
[/LIST]

To my great satisfaction, I heard my printer start up and before I knew it, I had the Ubuntu Printer Test page churning out of my printer! This worked for me. I hope it will work for you. The same logical approach may even work for other printer models. 

The main message is, with Linux, we can freely play around and with a bit of intuition and some time, we can get things to work.

All up, I only invested about 30 minutes of my Saturday morning to get my Fuji-Xerox C525A printer working. I hope you can get yours working too!

Bye!

PJ

---

### Post by kalex on 2011-03-31
Thanks for the post, it worked for me! I have just installed Ubuntu 10.10 (64-bit) on my HP dv6 laptop (Intel i7 core, not AMD) and was able to get my printer working, despite 'alien' refusing to extract the 32-bit rpm, by using your help.

-- keith

---

