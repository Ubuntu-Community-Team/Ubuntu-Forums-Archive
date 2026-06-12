---
title: "Is the NVIDIA GeForuce Go 7300 good with Beryl?"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by Espreon on 2007-07-06
Is it good with Beryl/Compiz-Fusion and other composite apps. What I mean is it good with Beryl and so on is does Beryl/Compiz-Fusion get good performance with that card. I need to know since my Mom is getting me an Ubuntu Pre-installed laptop for Christmas, and I can't live w/o Beryl/Compiz-Fusion,AWN,Affinity and other compositing apps!
It seems Nvidia offers Linux drivers for the card and I am not going integrated!

---

### Post by DagMan on 2007-07-07
I have that card.
Beryl is working for me.  It is running stable.  Initially I had a problem where I could not run emerald or heliodor which made beryl a useless thing to have.  I came accross a post here that suggested one command at the prompt and everything worked from there.  I don't know what that command was now, but there's no reason to think that you wont also run into the problem and need it and as it was difficult for me to find it may be difficult for you to track down as well.

I have uninstalled gnome-screensaver and installed xscreensaver so that I could edit xscreensaver to a custom script.  Even with the screensaver turned off, I had a probelem where screenblanking would lock me out of a graphical screen and all my virtual terminals.  Any manner of trying to keep the screen from blanking did not work.  I have xscreensaver run a script that first off, kills xscreensaver, runs a script I found for another beryl workaround which exports variables needing to kill beryl and bring it back with everything on the proper worksapces and locations on the workspaces, then my screensaver script changes to virtual terminal 6 and blanks the screen... it has to be done like this as xset just won't work and no matter how I try I can't get the results I want, it has to be done from the vt to do it properly.  It checks every one second for when I switch back to vt 7 and when I have it restores beryl and for some reason I have it restarting the panel but I don't remember why.

The suspend script also uses the script to export beryl variables, kills beryl, and on resume puts everything back.  
My suspend script also grabs a bunch of data from the proc filesystem about the video and shoves it back in on resume.  I don't know how it works and it was really old info regarding another nvidia card so I'm not thrilled about using it but I do.

After a resume, either from disk or from ram, I can ctrl-alt-backspace or restart gdm only once.  On the second time the graphics willl not start unless I switch to the nv driver.  Also after a suspend, the computer will hang on the last part of the restart process.  Shutdown works but restart will hang.  This is the same from the gui and the command line.


As you can see, and as with many laptops, it hasn't been without its problems.  Most of them are solved and the last real peev of not being able to restart the graphics more than once after a suspend, or restart after a suspend, I have given up on solving.

As I said before, beryl did not work out of the box with NVIDIA and I had to send it a command which I recall was actually disabling one of the many capabities.

As for how beryl runs, I am happy with it.  I wasn't as first with my previous system being an intel integrated graphics but I know that it will work much better on those systems anyway.  It is very good.  I have avoided some effects that don't look good such as magic lamp. Wobbly windows was difficult to get how I was happy with.
Integrated graphics actually are more the way to go with beryl from what I understand. 

Good luck, and if you go NVIDIA and it doesn't work at all, or even if you go integrated and it doens't work at all, rememeber that beryl isn't stable. Nor is compiz.  I wouldn't bank on effects when you make your purchase.  That said though.  It seems like the people with ATI cards have a hell of a time getting things to work.  Also, as you can see, having a graphics card was additional work in setting up.  Hours and hours of searching here and on google and I still have the mentioned problems which are annoying.

---

### Post by Espreon on 2007-07-08
Thanx, but with integrated chips, they put a penalty performance on the CPU and rest of the comp. And it was quite easy for me to setup Beryl/Compiz-Fusion with my ATI card with XGL.

Also are you using XGL with the NVIDIA or AIGLX?

---

### Post by Ocxic on 2007-07-08
I have that card it works great, no problems at all, with both the ubuntu driver and propetairy one.

---

### Post by DagMan on 2007-07-12
> **Espreon said:**
> Thanx, but with integrated chips, they put a penalty performance on the CPU and rest of the comp. And it was quite easy for me to setup Beryl/Compiz-Fusion with my ATI card with XGL.

Also are you using XGL with the NVIDIA or AIGLX?
I'm using XGL with the latest driver from the NVIDIA site.  
I formatted and did a clean install of Gutsy and so far, compiz worked out of the box and turned itself on after I installed the driver.  It had a little bit of a problem with the desktop not doing anything on boot occasionally so I gave beryl a try to replace it.  Emerald and helidor aren't installable from the repos yet but it's working fine with aquamarine in Gnome at the moment.  Ugly at first but okay with the Keramic theme right now.  I haven't tested everything in power management yet but everything in Feisty was working although sort of hacked around.  The problems I mentioned earlier seem to be mostly gone but it's too early to tell for sure.  What is remaining for sure is the need to do the thing on suspend to export beryl stuff then bring it back up on resume... killing beryl entirely and bringing it back or I get the same problem of a blank screen.  I haven't tested suspend with compiz or tested compiz starting after the gnome environment is up entirely and everything is drawn on the desktop... which I think will work but would require investigation into how compiz is starting now and I'm too lazy for it considering that I prefer beryl.  I also have not yet been able to test what happens when I resume from a successful suspend as I haven't yet had a succesful resume... I forgot to save my scripts when I formatted so here I am searching for that part again.

To make things short though, things on Gutsy aren't stable and there are still crashes here and there, some relating to compiz.  Compiz works well but I think it just needs to wait a little longer before being started and that will solve the little problem with it.  Hopefully this will be done before Gutsy is released.  The card works with these things and where the kinks aren't ironed out, there are most certainly ways to work around.

This almost does some of it 
[http://ubuntuforums.org/showpost.php?p=2124512&postcount=7](http://ubuntuforums.org/showpost.php?p=2124512&postcount=7)

---

### Post by klato on 2007-07-12
I've got a system76 gazelle performance which comes with an nvidia geforce go 7300.

It worked very well with Beryl, but sometimes there would be a skip...although I think that might have had something to do with Beryl itself, because now I'm running Compiz Fusion and it runs basically flawlessly for me.

As for integrated graphics, from what I understand, those graphics solutions eat up your system memory because they do not have their own video memory.  The 7300, however, has it's own dedicated memory.

Hope that helps.

---

### Post by Ocxic on 2007-07-12
I just installed compiz fusion, it's working great, and has replaced beryl now....

except that i have to run  compiz --replace -c emerald twice each time i login.

hopefully the update i just installed fixes that, i think it more of a slight conflict with my beryl install.

---

