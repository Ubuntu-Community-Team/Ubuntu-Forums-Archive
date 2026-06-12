---
title: "Compiz  graphical problems,  on a new install(8.10)"
date: 2008-11-01
forum: General Help
---

### Post by ram130 on 2008-11-01
I don't know  what is causing  it but  i never had this problem in 8.04. Can someone please help me.  I  am runing on AMD althlon Xp 2000+, 768MB DDR RAM, Nvidia GeForce 5200FX and Compiz 0.7.8(1:0.7.8 ).  I know the  machine is old. The screen shot below will  show  you what i am talking  about.Also i didnt change anything to compiz, jus enable it. If i need to upgrade please tell me how because I only see 7.8 in da package manager [[IMG]http://img91.imageshack.us/img91/8159/ubuntuproblemhq6.th.png[/IMG]](http://img91.imageshack.us/my.php?image=ubuntuproblemhq6.png)[[IMG]http://img91.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by mihaiv on 2008-11-01
What kind of graphical problems? I don't get it from the screenshot.

---

### Post by ram130 on 2008-11-01
look in the title bar in Mozilla. Or right where my mouse  is.

---

### Post by tom56 on 2008-11-01
I'm having the same problem. I'm not sure what's causing it but it happened after I enabled the nvidia driver - so it's either the driver or the effects that come with it that are the issue.

---

### Post by ram130 on 2008-11-02
anyone got any fixes?

---

### Post by Acejam on 2008-11-02
> **ram130 said:**
> anyone got any fixes?

I'm also having this issue. Not sure whats causing it, but I'm running Ubuntu 8.10 with "extra" desktop effects, and a restricted Nvida driver. Very weird.

---

### Post by Zunino on 2008-11-02
Here's another user who's been experiencing the same annoying visual glitches with Compiz/nVidia on Intrepid Ibex. I have tried a couple of solutions proposed in other threads (such as adding the 'AddARGBGLXVisuals' option to xorg.conf), but nothing worked. For the moment, I guess I'll just live without the special effects.

Anyway, I'll be listening to this thread in case a working solution pops up.

Regards,

-- 
Ney André de Mello Zunino

---

### Post by outerspacerace on 2008-11-02
I'm getting this exact same error also, with both the nVidia driver 173 & 177. This problem didn't exist in Hardy for me either.

I'm yet to try turning compiz off. 

When I get home I'll try that and using some emerald themes to see if that's a workaround for now.

---

### Post by the_arm on 2008-11-02
Count me in with the same problem, too.
It's strange because it isn't EVERY time I select a window...just some times.

GeForce 7100 GS, using the 177 driver.

Everything was just fine under 8.04; just did the upgrade to 8.10 today.  I haven't played around yet with compiz too much yet to see if I can get it to go away, but I'm not optimistic considering the other posts here!

I just subscribed to this thread in case someone figures out a solution!

thanks,
arm

---

### Post by psoplayer on 2008-11-02
I've got the same bug on Intrepid running on an integrated GeForce 6150. The window decoration will glitch out randomly when moving the mouse onto or off of any part of the title bar that has a tooltip (icon on the left, minimize button, maximize/restore button, close button).

The big difference for me is that ***I did have this bug in Hardy***. I'll keep looking for a solution and I'll be subscribed here as well.

EDIT: Found the same issue on an nVidia forum. It seems to be a driver issue. [http://www.nvnews.net/vbulletin/showthread.php?t=104822](http://www.nvnews.net/vbulletin/showthread.php?t=104822)

---

### Post by outerspacerace on 2008-11-02
If you follow that right through you'll see an nVidia dev weighing in on the issue many times.

Basically, it seems like a slight workaround was submitted for the new drivers (which has made things worse for most of us) but more work is to be done on the issue.

He mentions it's a problem involving X and Compiz more so - I'm guessing a fix could be a while off :(.

Nice to know they're working on it though.

BTW is it hard to revert back to an ealrier driver? From memory I think they said 164 or so... I don't need anything much, not bring a huge gamer, just the basics working.

---

### Post by Sava8420 on 2008-11-02
> **ram130 said:**
> I don't know  what is causing  it but  i never had this problem in 8.04. Can someone please help me.  I  am runing on AMD althlon Xp 2000+, 768MB DDR RAM, Nvidia GeForce 5200FX and Compiz 0.7.8(1:0.7.8 ).  I know the  machine is old. The screen shot below will  show  you what i am talking  about.Also i didnt change anything to compiz, jus enable it. If i need to upgrade please tell me how because I only see 7.8 in da package manager [[IMG]http://img91.imageshack.us/img91/8159/ubuntuproblemhq6.th.png[/IMG]](http://img91.imageshack.us/my.php?image=ubuntuproblemhq6.png)[[IMG]http://img91.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Ok so this appears to me like the problem is actually quite simple.  Do you by chance have the ememrald theme manager installed?  If not emerald theme then one that is similar to it?  What you need to do is go to your theme manager and under preferences or options there should be a check box for transparent buttons along with a time setting for transparency.  Uncheck the check to disable button transparency and problem should be gone.  It is often checked by default upon installation of some theme managers.  Good luck.  If you can not find a theme manager settings tab then go to system/preferences/main menu and go through the tabs to make it available.  Hopefully this will solve your problems.

---

### Post by Arl on 2008-11-02
I had the same problem; I think what I did was just re-loaded Compiz-Fusion Icon. I know this seems simple, but sometimes we over look the simple things.

---

### Post by orion2087 on 2008-11-02
I'm having the same problem and haven't installed anything like the compiz-fusion icon. I just installed the nvidia drivers and effects right out of a fresh install.

---

### Post by ed4567 on 2008-11-02
I'm having a similar problem and I do NOT have an nvidia card in my laptop. 
Mine is a 
 Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

Still, the problem I'm having is that after an upgrade install of 8.10 I have no window controls at all, the whole window title and control button section of the window is gone... completely. If I click where it should be it doesn't bring the window into focus either... so it's obviously not just invisible. 
I wonder if this is the same issue or something different entirely. I tried completely removing and reinstalling compiz but it didn't change it. I also tried checking and unchecking things in the compizconfig settings manager and that didn't work either. 

Anyone have any thoughts or should I post this as a different thread?

Ed

ok, not sure if this works for anyone else, but for me I installed the "compiz fusion icon", once I started it my window controls came back just fine. Something about resetting the window decorator to gtk?

Anyway, hope this helps someone else too.

---

### Post by outerspacerace on 2008-11-03
I tried installing Emerald Theme Manager like I mentioned in my earlier post here and yes, once you do that the problem disappears... except for some themes getting garbled in Open Office applications. 

This has been happening since I switched to ubuntu at 8.04 however. One emerald theme I have and really like called "Community" is by far the worst culprit. I don't know why except to guess that it has something to do with Java maybe?

Sava, I couldn't find the option you mentioned from a quick look just now.

I'm not so sure that's the whole problem anyway - like Orion I got the problem from a fresh install and by simply enabling nVidia drivers.

(Note: I could be wrong on that one, there's a small chance I'm not correctly remembering the order in which I did things after the install lol)

Anyway, I don't really wanna have emerald themes applied this time round - I tend to tweak/change them too much plus I wanted to keep the default look!

So I guess I'll install the Compiz Icon and give that method a try.

Having said that, we really shouldn't be needing to mess with things like that to keep the default look of an OS intact :(

---

### Post by outerspacerace on 2008-11-03
Arrgh I was getting confused, have been working away setting 8.10 up too long now lol!

I don't think the Compiz Fusion Icon is the answer at all, except for it illustrating things a bit clearer.

For me you can have it "Select Window Decorator" as either GTK or Emerald and there is NO problem - as long as Metacity is the Window Manager.

It's the Compiz option in "Select Window Manager" section that starts all the issues decribed in this thread.

For people reporting that making GTK the window decorator fixed it, they must not have Compiz on at the same time.

My problem is I want the 3D effects that Compiz offers AND the clean look of the default GTK decoration in unison.

I can't currently have that, if I want 3D effects then I must use Emerald as the window manager.

That leaves me with about 20 themes of downloaded so far to choose from, most of which either look horrid or just like Vista :(

---

### Post by nickstephens on 2008-11-03
OK, there are more people with the same problem. Reassurring I suppose :-) 

I have multiple machines but the laptop running the hardy 8.04 only displays this problem. I have tried to install the fancy 3d cube screen graphics but and I can't honestly remember wether the problem was there before or not. I do know that the problem is occurring more frequently now, and seems to be provoked by firefox applications. This could be simply a case of firefox being the most used application :-s

---

### Post by the_arm on 2008-11-03
Outerspacerace - I was getting confused as well; and I agree, the Compiz Fusion Icon doesn't do anything to SOLVE the problem, but it at least makes the interactions a little more clear.

For what it's worth I installed some other themes and found a couple that didn't have the issue.  One is the "Kin" theme that was in the thread that psoplayer recommended earlier in this thread ([http://www.nvnews.net/vbulletin/showthread.php?t=104822](http://www.nvnews.net/vbulletin/showthread.php?t=104822)) which you can get by installing community-themes.  Didn't particularly care for it, though; it was too orange for me.

Instead I ended up installing this theme: [http://gnome-look.org/content/show.php/Shiki-Colors?content=86717](http://gnome-look.org/content/show.php/Shiki-Colors?content=86717)  which I found recommended somewhere else on ubuntuforums - but I've lost that thread.  It doesn't seem to have the problem, either.

(meaning, in both cases I can leave compiz on and not randomly lose my title bars.  Note that I am NOT using emerald as the window decorator in this case, just GTK and switching with System-->Preferences-->Appearance)

I'm guessing we could probably fix "human" if we were to load it into emerald and then edit it the way that Sava8420 recommended below.  But, I wasn't sure where to get human as a tar.gz so that I could drag it into emerald.  I installed emerald and didn't see any themes listed there to play around with and instead got sidetracked when I found the shiki theme.

I'd be happy to play with it if someone knows where you grab human that can be seen by emerald (or give me advice as to how I installed emerald wrong.)

-arm

---

### Post by mikewhatever on 2008-11-03
Take a look here [http://ubuntuforums.org/showthread.php?t=875741&highlight=compiz+title+bar](http://ubuntuforums.org/showthread.php?t=875741&highlight=compiz+title+bar). It seems to work so far.

---

### Post by abh83 on 2008-11-03
I'm having the exact same issue. In my case its related to the default GTK window decorator. I have an nvidia GeForce Go 7300.

I tried installing the fusion icon and refreshing the window manager with no luck. However, it seems not all themes/theme-engines are affected.

Btw... i don't get it but whats up with nvidia drivers and ibex 8.10? what did they change in this new release?

---

### Post by Dvorakis on 2008-11-03
This is rediculous...im so used to having AWN...and these graphic bugs are making it so hard to be productive...We need a fix soon.

---

### Post by Elessor on 2008-11-04
I also had a Compiz related issue after a clean install.

Running:
Intel D945GCLF2 MB with 2 GB Ram
Intel 945GC chipset: 82945GC Northbridge with integrated GM 950 graphics

Install went okay.  Later when I went to play around with the Compiz Advanced Settings Control so look at the much vaunted cube things went south.  After making the changes and clicking apply the computer rebooted on it's own and then went to the Log In screen.  After logging in startup proceeded to desktop without panels, then the screen went to "jibberish" (for lack of a better description).  Then it would return to the Log In screen and repeat the process.

I had to remove Compiz to get up and running again.

Any thoughts?

---

### Post by Zunino on 2008-11-05
Hey all...

Just some minutes ago, I forced a refresh of the package information on Synaptic and was pleasantly surprised to find out there were updates available which included the **Human Theme**. For a moment, I thought our problems might be over. I installed all the suggested updates and then restarted the graphical environment, but to no avail. The title bar glitches still pop up just the same. I don't know for sure what changed in the new version of the theme. Nothing that I have been able to notice. Plus, the "list of changes" was not yet available from the update manager dialog.

Well... I'd rather be the bearer of good news, but anyway, I just thought you guys should know. In any case, if somebody's experience is different, please share it.

Regards,

-- 
Ney André de Mello Zunino

---

### Post by davidevan on 2008-11-05
I had this exact problem in Gutsy Gibbon but the problem disappeared in Hardy Heron. I'm also using an nVidia video card. I'm glad I'm not the only one with this problem.

---

### Post by ram130 on 2008-11-06
> **Sava8420 said:**
> Ok so this appears to me like the problem is actually quite simple.  Do you by chance have the ememrald theme manager installed?  If not emerald theme then one that is similar to it?  What you need to do is go to your theme manager and under preferences or options there should be a check box for transparent buttons along with a time setting for transparency.  Uncheck the check to disable button transparency and problem should be gone.  It is often checked by default upon installation of some theme managers.  Good luck.  If you can not find a theme manager settings tab then go to system/preferences/main menu and go through the tabs to make it available.  Hopefully this will solve your problems.

no i dont use any theme manager, just a fresh install on the system with the recommended latest nvidia version 173 and compiz.

---

### Post by CoolDreamZ on 2008-11-06
The corrupted title bar problem has been around for a while, but it just got **much worse** for me with 8.10 Desktop AMD64. I suspect the newer nvidia drivers are causing the problem. I have reverted to 8.04.

See this thread for more details:

[http://ubuntuforums.org/showthread.php?t=591765]("http://ubuntuforums.org/showthread.php?t=591765")

---

### Post by paranoid_humanoid on 2008-11-07
i have the same problem on ubuntu intrepid. never had it on hardy..
i have a nVidia geforce 6600 graphics card.. this is totally unacceptable and really irritating :mad:..

---

### Post by sharkster2007 on 2008-11-07
I have and Nvidia 6600GT (AGP) graphics card and suffer the same problem. Think its down to Nvidia and their driver. :-(

---

### Post by kiran88pnjr on 2008-11-07
I am currently using Ubuntu Intrepid Ibex. I have the video card of nVidia GeForce 6150 SE with 512 MB video memory. 1 GB Ram IS my memory. I have been  NVIDIA ACCELERATED GRAPHICS DRIVER 177. But I doesn't have any problem with that. My desktop effects work perfectly using this driver.I am using Compiz 0.7.8 and Emerald Theme Manager.:popcorn:

---

### Post by outerspacerace on 2008-11-10
I just installed 64bit 8.10 finally (wanted to make use of some extra RAM I have now) which works great. It prompted me to install the nvidia drivers as normal, then after rebooting the older set was offered also (.96? I forget now) so I opted for those drivers which seemed to be working great now.

---

### Post by Zunino on 2008-11-11
Hi.

Moments ago, the restricted drivers icon showed up on the notification area informing me that there were other driver versions available. I opened the hardware drivers applet and picked the "new" item, 'NVIDIA accelerated graphics driver (version 96)'. After rebooting, I went straight to the theme selection dialog and picked the standard Human Theme. That's it. Compiz is working great and there are no more issues with the title bar of windows (as far as I can see). Even the Thunderbird composer window behaves well as you type in the email's subject.

I think that's the best thing we can have until NVIDIA provides a proper fix to the newer drivers.

Cheers and good luck to all,

-- 
Ney Zunino

---

### Post by catchagato on 2008-11-16
I tried installing the 96 nVidia driver from Synaptic Package Manager, but still no luck... I have a Thinkpad T61, with a nVidia Quadro NVS 140M card. If anyone has tried anything else, please post your results even if it didn't work.

---

### Post by IceReaver75 on 2008-11-16
I was haveing alot of the same problems with glitchy title bars when using the human theme with the 177 drivers.  So i tried switching to the 96 drivers and the glitchy title bars went away but all the menu options in open office disappeared so neither driver was working correctly.  One driver fixed one problem but caused another.  So I went to the Nvidia site and they have availble for download the 180 beta driver.  It says it fixes window problems in the geforce 6xxx and 7xxx cards.  I downloaded it and got it installed after alot of reading on how to install a downloaded nvidia driver.  Rebooted the x server and everything is working well now.  No more window glitches with human theme and all the menu options are there for open office.  That driver has seemed to fix everything that I was having problems with and not causing any others that I have noticed.  I open and ran almost every program to check and all is fine.  Anyone using the Nvidia 6xxx or 7xxx cards and aren't afraid to manually install the driver might want to give the 180 driver a try and see if it fixes your problems.  I don't even get the title bar turning clear/pink with open office anymore, and all compiz options are working fine.

---

### Post by noorez on 2008-11-17
Hey, I have this a shot. It installed fine, but when I turned on compiz, I found that the desktop was being drawn incorrectly i.e. The current workspace and part of the one next to it were being drawn crunched up together. Any idea's how to fix it? It seems to work well for you?

---

### Post by noorez on 2008-11-18
opps...it appears i fixed it. Under nvidia-settings i changed resolution from auto to 1280x800 (the resolution I know my screen is for sure). This fixed the problem. This might be a bug in this driver( resolution not detected properly).....to bad its not open source.......

---

### Post by loomsen on 2008-11-18
[Here's how to fix permissions](http://ubuntuforums.org/showthread.php?t=985737)
which are too restrictive by default. Often this might be a problem as well.

---

### Post by skbeez on 2008-11-18
I downloaded emerald theme manager and compizconfig settings manager from synaptic package manager. Then in the Window Decorations menu in compiz config, I typed "emerald --replace" in the command section. Now all is well!! Hope this helps

---

