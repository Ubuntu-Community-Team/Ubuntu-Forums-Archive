---
title: "[SOLVED] Maintenance mode comes everytime Cairo dock."
date: 2008-08-13
forum: General Help
---

### Post by diwas on 2008-08-13
I downloaded and installed Cairo Dock from 
[http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)

But after the package is installed the "Maintenance mode" comes up everytime whether i QUIT the program or press OK.

What is the problem?

Thank you.

---

### Post by diwas on 2008-08-14
It works now...though i dont know the problem.

here's how it worked.
i removed cairo-dock from the synaptic...then removed all its settings:
```

sudo rm /home/.cairo

```

then reinstalled it.
And it works.

---

### Post by eentonig on 2008-10-30
I have the same issue.

---

### Post by diwas on 2008-10-31
The solution is mentioned above...
I hope it wud be helpful.

---

### Post by diwas on 2008-10-31
The solution is mentioned above...
I hope it wud be helpful.

---

### Post by rjklindsay on 2009-03-24
I tried upgrading from Cairo-dockV2.0.0-beta0 to Cairo-dockV2.0.0-beta3.1 when I ran into this same problem whereby <Maintenance mode> keeps popping up in a loop.

The following code had no effect for me:
  sudo rm /home/.cairo

However, deleting /home/.config/cairo-dock ALMOST solved the problem.
The next time I started cairo-dock2 (beta3.1), a different window poped up, which let me download and install a new theme. But after installing the theme, the <Maintenance mode> window pops up again, and wont go away.

The final solution for me, was to go back to using the slightly older beta0 version.  Unfortunately this version is no longer available for download, but I'll be happy to email my copy to anyone who wants it.

---

### Post by fabounet on 2009-03-25
probably launching it with
cairo-dock -c
will help you

some drivers are really crappy and make the dock crash at startup.
Fortunately things are getting better with Jaunty.

---

### Post by rjklindsay on 2009-03-26
Thank you Fabounet.
Your suggestion solved the problem.

---

### Post by A55umer on 2009-04-16
My stack plugin crashed me. turned it off in maintenance mode and a winrar was me.

---

### Post by JakcV on 2009-05-19
Use no open-gl can really solve the problem. Thanks.

---

### Post by caaloss on 2009-09-03
Hi DIWAS...  I did just what you said
 
but when I type in the Terminal sudo rm /home/.cairo  nothing happens, I just got this message  

rm: cannot remove `/home/.cairo': No such file or directory

I used the Add/Remove applications from the applications menu tu install cairo-dock

---

### Post by fabounet on 2009-09-04
it's ```
rm -rf /home/.config/cairo-dock/current_theme
```
if you need to restart from scratch.

---

### Post by Pifilatakanemu on 2009-10-08
The
cairo-dock -c
and to start without open-gl 
didn't solve my problem.


Any other suggestions besides starting from scratch again?

After starting cairo i get this output in the terminal:

```
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:327)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-internal-accessibility.c:get_config:71)  
  The option 'auto-hide' is in conflict with the 'raise on shortcuts' option, it will be ignored
cairo-dock: jpc_dec.c:1072: jpc_dec_tiledecode: Assertion `dec->numcomps == 3' failed.
warning :  (cairo-dock.c:_cairo_dock_intercept_signal:176)  
  Cairo-Dock has crashed (sig 6).
It will be restarted now.
Feel free to report this bug on cairo-dock.org to help improving the dock !
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:327)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
debut de boucle bloquante ...
```

---

### Post by fabounet on 2009-10-10
try
cairo-dock -c -l debug
and paste the output here, maybe there is some clue

---

### Post by subspaceeddy on 2009-12-04
@flohmann: did you solve the problem? I had the same problem, with a simiar error message, and the issue was basically a settings conflict for me. the line:
> The option 'auto-hide' is in conflict with the 'raise on shortcuts' option, it will be ignored
cairo-dock: jpc_dec.c:1072: jpc_dec_tiledecode: Assertion `dec->numcomps == 3' failed.
warning :  (cairo-dock.c:_cairo_dock_intercept_signal:176)  
  Cairo-Dock has crashed (sig 6).was the clue.....

To fix this, whilst the maintenance page is up, click 'Accessibility' (under 'Behaviour') and untick 'Keep the dock below other windows ?' (under 'Pop-up'). Click Apply/OK and restart.

I guess unticking 'Activate auto hide ?' might also fix this since the crash is caused by a conflict between the two.

Hope this helps...

---

### Post by puffead on 2009-12-08
i had this same problem if you go to 
1. /home/.config/cairo-dock
2. open current theme folder
3. select and delete its contents
4. go to themes folder, and choose one
5. copy and paste a theme from themes folder into current theme folder
6. launch program

---

### Post by mdalacu on 2009-12-13
Puffead's solution worked perfectly for me, but i have to mention that theme folder is **/usr/share/cairo-dock/themes/_default_** not */home/xxxxx/.config/cairo-dock/themes* which was empty.

---

### Post by fabounet on 2009-12-13
/home/xxxxx/.config/cairo-dock/themes  is where themes are stored
avoid modifying files in /usr, it is the root domain
if the dock doesn't start with your theme, even with "cairo-dock -c", please make a tarball of it and post it somewhere or send it to me, it could help !

---

### Post by mdalacu on 2009-12-18
> **fabounet said:**
> /home/xxxxx/.config/cairo-dock/themes  is where themes are stored
avoid modifying files in /usr, it is the root domain
if the dock doesn't start with your theme, even with "cairo-dock -c", please make a tarball of it and post it somewhere or send it to me, it could help !

what i was trying to say:

$ sudo killall cairo-dock
$ cd /home/XXXXXX/.config/cairo-dock/current_theme
$ rm * -rf
$ cp /usr/share/cairo-dock/themes/_default_/* . -rf

now, restart cairo-dock !

---

### Post by Josunik on 2010-01-03
I removed the whole cairo from synaptic, marked all cairo packages for complete removal, then restarted the system, tried a fresh installation from synaptic again, and nothing, every time I open the cairo-dock the maintenance windows comes up, and wont go unless I kill it.

For now I just uninstalled everything until further notice

note:

1st installation was OK, problem started after first reboot, 

Ubuntu 9,10
Nvidia graphic card 7900
hp pavilion running on AMD
3GB RAM

---

### Post by fabounet on 2010-01-03
hmm, reinstalling won't change anything, you're not under windows.

but if you're going to reinstall, try to install the PPA package on launchpad.
you'll get the latest version.

also, try cairo-dock -c -l debug, and post the result here.

another thing  when the config panel comes up, try deactivating all the appplets.

---

### Post by eyerouge on 2010-01-05
> **subspaceeddy said:**
> 
To fix this, whilst the maintenance page is up, click 'Accessibility' (under 'Behaviour') and untick 'Keep the dock below other windows ?' (under 'Pop-up'). Click Apply/OK and restart.

I guess unticking 'Activate auto hide ?' might also fix this since the crash is caused by a conflict between the two.

Hope this helps...


Fixed it for me (I'm using Jaunty and whatever Cairo is in the Jaunty-repo)

---

### Post by firebug2 on 2010-01-11
I just had the same issue upon restart after updates on Karmic.  What I think (fabounet as a member of cairo-dock team could correct me if I am wrong) is that cairo-dock auto-restarts in maintenance mode in certain situations when something in configuration fails (e.g. missing parameters or parameter conflict).  Naturally, this may occur under variety of circumstances and thus different solutions will work.  Ultimately, cairo-dock of the future will be so smart as to direct a not-linux-savvy user which parameters to fix, or maybe even fix conflicts automatically :D

I describe how I "fixed it" (in fact, I don't know what the exact problem was).

1. To get out of the loop of popup configuration windows (note to cairo-dock team: perhaps there should be some way to quit program altogether when in maintenance mode, otherwise it just keeps you running circles and creates extra processes), open a terminal window and kill all the docks:

```

ps -Af | grep cairo-dock | grep -v grep | awk '{print "kill",$2;}' | bash -sf

```This step allows me to start cairo-dock from a terminal to see the output.  WARNING: this command will kill all the processes that have "cairo-dock" in their command.  On my system this only includes the currently runnig instances of cairo-dock, this may be different on yours.  If worried, just do "ps -Af | grep cairo-dock" and kill processes manually (or if you have more time, use gnome-system-monitor).

2. In my case it failed with and without openGL, so I just start as (in my case "-l debug" didn't provide any additional insight but it may help you)

```

cairo-dock -o

```and watch the output.  In my case the error was 

> Assertion 'pthread_setspecific(t->key, userdata) == 0' failed at pulsecore/thread-posix.c:200, function pa_tls_set(). Aborting.So I thought this has something to do with pulseaudio.  Accordingly, I...

3. ...disabled AlsaMixer and bingo!  It restarted fine.

4. The twist is that I then enabled AlsaMixer (I do like the ability to change volume by mouse scroll - it works on the gnome panel too, however).  At first everything was fine but then it crashed again as I was writing this.  So I disabled it again and everything seems to be fine for now.

I may play with this later on by messing with the AlsaMixer configuration (~/.config/cairo-dock/current_theme/plug-ins/AlsaMixer/AlsaMixer.conf) and will report if I find anything interesting.

PS.  I tried to further track down the issue by killing ("pulseaudio -k") which used to work to recover sound when pulseaudio broke it in Hardy (still not fixed afaic), but on Karmic this just kills the sound completely.  I guess in my case the issue may be that some changes in pulseaudio made AlsaMixer controller incompatible with it.  I'd be glad to track down the specifics further if someone from cairo-dock team tells me where to look.  I checked the contents of the pulsecore/thread-posix.c, but can't deduce anything other than there was some parameter it expected but did not receive.  I *did not* try the "nuclear option" of removing .config/cairo-dock/current_theme or reinstalling the whole thing and I am not inclined to do such a micro$oftish exercise.

---

### Post by fabounet on 2010-01-11
thanks for the hint, I didn't know that pulseaudio could crash the applet.
I don't think it has something to do with the config of the applet, or even with the applet I'm afraid.
the aplet merely uses libalsa in a normal way, and the crash probably occurs inside libalsa.
This might be relevant to notify the devs of libalsa and pulseaudio (they probably are a bit buggy since I also can't use Pulseaudio in my music player without a huge CPU consumption)

---

### Post by jediknight64 on 2010-01-17
I truly thank you firebug. Disabling AlsaMixer solved that very problem I was having. As soon as I clicked on it, my dock popped right up! It pays to comb these forums. Thanks again.:D

---

### Post by fabounet on 2010-01-17
this bug should be reported to pulseaudio devs.
if you can provide them with all the details you have, it may be very helpful.

---

### Post by TD Symbolik on 2010-04-09
Just removed it and installed Avant Window, worked great with my OS X theme!!! Thanks for the help!!!:lolflag:

---

### Post by mathiasbc on 2010-07-08
Hi, well to tell you guys that my solution was to untick "show currently opened applications in the dock" , somehow when the download page appeared, because i was downloading something, the dock just crushed, followed the cairo-dock -c -l debug and found that the problem was with the actual download page that firefox provides.

Hope this helps.

---

### Post by Cpierce on 2010-09-11
Just to let everyone know, this post was very helpful.

---

### Post by ubialan on 2010-12-29
what worked for me was i had to choose a theme hit apply it now works!

---

### Post by ubialan on 2010-12-29
sorry a little incomplete instructions when cairo dock pops up in maintenance mode go to themes choose one closed it and started cairo dock and it worked

---

### Post by krishbala on 2012-03-04
Just a correction..
me too experienced the same problem..
me just disabled the desktop switcher in my cairo..
thats all now everythin' is workin' fine..
kinda happy..

---

### Post by oldos2er on 2012-03-04
Closed, necromancy.

---

