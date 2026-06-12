---
title: "&quot;Smeared&quot; text in 9.04 install"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by rayj0007 on 2009-04-28
Just installed 9.04 and it seems to work fine except ALL the text appears to have some of the pixels in the opposite color. My guess is the file that defines the text appearance is corrupted. Help needed and appreciated

---

### Post by shatterblast on 2009-04-28
Assuming no drivers for graphics hardware have been installed, you might disable Compiz.  To do so, go to:

System -> Preferences -> Appearance -> the Visual Effects tab -> set to None.

---

### Post by rayj0007 on 2009-04-28
Shatterblast,

That solved the problem. 

Interesting it only showed in the alphanumeric characters.Beyond me. 

Thanks very much!

---

### Post by shatterblast on 2009-04-28
It might be how Compiz relates to your video drivers.  There are a few minor inconsistencies remaining to be smoothed out still on the Ubuntu side of things.  If you have Intel as your graphics hardware, that could be the reason.  Otherwise, it might be good to visit:

System -> Administration -> Hardware Drivers

From there, you may have the option to enable your graphics hardware.  Just be warned that a lot of troubleshooting may follow after if something "activates" incorrectly.  If it works well, it may be good to turn on again the Visual Effects in Appearance.

---

### Post by rayj0007 on 2009-04-28
Sad news, the problem came back when I opened my Firefox browser.

When I close Firefox and reboot the problem goes away until I open Firefox again. The problem remains after I close Firefox until I reboot.

The Firefox error console gives the message:

Error in parsing value for property 'text-align'.Declaration dropped.

It indicates the problem is in line 25 (below).

#Links {padding-top: 80px;text-align: middle;}

Am I in the right place for this problem or should I report this as a bug?


P.S. This problem also affects the text in Firefox.

---

### Post by shatterblast on 2009-04-29
The problem might relate to JavaScript or add-ons specifically to Firefox then.  The following assumes you are using the latest Firefox version, which is 3.0 or higher.  My version is 3.09.  To test for this:

Open FireFox -> Click Tools across the top -> click Add-ons in the menu -> click the Plugins "tab" across the top of the window in case you're not there -> proceed to click Disable on everything in that list.

After all things in that list are disabled, reboot the computer.  Try FireFox again.  If you have the same problem, let's change the home page to the default.  You might want to "copy and paste" your original home page into a blank document so you can put it back later.

To do so:

click Edit across the top of Firefox -> select Preferences at the bottom -> click the Main "tab" across the top of the window -> "copy and paste" your home page address into Text Editor or something to back it up if you want, and don't forget to Save  -> click the button where it says Restore to Default.

After pressing Close or whatever, reboot the computer again.  Please report the results.  It might be that your plug-ins need updating in some fashion, especially JavaScript.

---

### Post by rayj0007 on 2009-04-30
Disabled all plugins.

Had previously changed Firefox to open on blank page.

Firefox is v 3.0.10

All updates are installed.

Problem persists.

I also noticed the problem develops over time with just Evolution open.

A defective character shows the same defect at all locations.

I am going to try running a live session and see if the problem develops. Will report results.

Thanks for the attention to my problem.

---

### Post by shatterblast on 2009-04-30
If you upgraded from a previous version, can you please add what version?  My next thought would be something in the xorg.conf file, but that might be getting too deep too early.

Or else, did you do a clean install over a previous version?

---

### Post by rayj0007 on 2009-04-30
Did a new install over a 7.x version.

Ran a 9.04 live disk session and it had the same problem so I believe the problem is with the download.  I downloaded on a windows box and I didn't run ck5sum to check the file. Shame on me. 

Sorry to put you to the unnecessary effort.  I'll work on getting an error free file installed and take it from there.

Thanks again for your help.

---

### Post by c-fstb on 2009-05-01
Just so you know you're not alone with this issue. This is my first post in the ubuntu forums, so I hope this isn't considered rude to jump into your thread but I have the exact same issue so I'm hoping that by adding my info somebody can figure this out. 
 I updated from 8.10 last week and immediately had this issue. It only seems to affect Firefox and Evolution as well as the top & bottom panels. It is always fine after start-up or reboot, but gradually a few text items will begin to become corrupted, then more until it becomes unreadable, but occasionally it will suddenly clear up on it's own. Right now, it is only all the capital "T" & "V" 7 "3" that are being affected, but it can be any character at other times. It looks like they are being highlighted in light grey. But this highlighting gradually becomes darker as well until it becomes black. Occasionally it also affects icons as well.
  I have found an oddity on the fonts tab under the appearance preferences. When I first open it all four choices are always selected under rendering. I can pick subpixel smoothing (LCDs) and usually most of the problem will go away, but not always. Going to the detail menu, under Hinting, "Slight" is always picked. Picking "None" or "Full" will also often make most of the problem go away. Strangley though these picks are not saved, as the next time I check them I always find all 4 rendering choices selected and slight hinting. 
  My system info, in case it helps;
Sony Vaio
Pentium III  1200MHz
369.7 MB memory
30 G HD
Release 9.04
Kernel Linux 2.6.28-11-generic
GNOME 2.26.1
FireFox 3.0.10
Evolution 2.26.1

Could rayj0007 also post more system info?

I just called away to do a job for an hour and upon my return I find that all text is perfect now, go figure. But I won't hold my breath that it'll stay that way.

---

### Post by shatterblast on 2009-05-01
To rayj0007:

If you continue having problems, is Intel the basis of your graphics hardware?  I would also suggest not reinstalling Jaunty if you continue with the issue on a different Live CD.  I think Jaunty 9.04 has a sensitivity to Intel, but my understanding is that it only applied when hardware acceleration occurred for specifically supporting OpenGL among other things.

---

### Post by shatterblast on 2009-05-01
I wonder if there is a package specific to Gnome causing visual distortion.  My first thought would be to experiment with Kubuntu, but I'm not experiencing the issue.  GTK is the only idea that comes to mind that links the two, and of that, it would have to be what is running GTK that causes the problem.

Still, that might point to a problem with Intel graphics in any direction.

---

### Post by emarkay on 2009-05-01
Have we confirmed that both these posters have Intel graphics here?

---

### Post by c-fstb on 2009-05-01
Yes I believe I have Intel graphics. Attached is a screen shot of Evolution that is currently corrupted.

---

### Post by rayj0007 on 2009-05-01
I downloaded another 9.04 and the hash says the file is error free.  The problem exists while running a live session from the new error free 9.04. The problem appears to be related to my hardware.

Pentium III (Katmai)
371.2 MiB

The graphics card is a Radeon N625

P.S. I ran a live session with 8.04 and had no problems.

I will continue to work with this forum to solve this problem if it will benefit the community, but I would be happy going back to 8.04. Let me know if there is benefit for the community.

---

### Post by shatterblast on 2009-05-02
> **rayj0007 said:**
> I downloaded another 9.04 and the hash says the file is error free.  The problem exists while running a live session from the new error free 9.04. The problem appears to be related to my hardware.

Pentium III (Katmai)
371.2 MiB

The graphics card is a Radeon N625

P.S. I ran a live session with 8.04 and had no problems.

I will continue to work with this forum to solve this problem if it will benefit the community, but I would be happy going back to 8.04. Let me know if there is benefit for the community.

It may be wise to stay with 8.04 for now.  Intrepid 8.10 is similar to Jaunty 9.04 at the moment if you want to experiment.  For compatibility, 8.04 might provide the best in avoiding complex troubleshooting.

Even for Microsoft, certain types of ATI Radeon cards group with Intel chipset drivers in my personal memory.  This usually relates to if the ATI graphics resides on the computer's main board itself.  This results in a mix of ATI graphics software and tweaks with mostly Intel hardware.  It exists because ATI and nVidia both to some extent allow other businesses to manufacture the technology for them.

---

### Post by hicksj678 on 2009-10-17
Not sure if it is appropriate to post here but as the two above users I am also having issues. Its almost as if its not drawing right. If I click or hover the text clears up.  My system Specs are 

[FONT=Arial, Helvetica, sans-serif][SIZE=2][COLOR=Black]**[]("http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=3827134&SRCCODE=WEBLET03SHIP&cm_mmc=Email-_-WebletMain-_-WEBLET03SHIP-_-03ship")**[/COLOR][/SIZE][/FONT]
AMD Athlon 64 X2 5200+
Biostar MCP6P-M2 motherboard
On Board GE Force 6150
2 gigs ram

I am also running 9.04 (64 bit) downloaded Oct 16 2009 


Should I also try a previous version

---

