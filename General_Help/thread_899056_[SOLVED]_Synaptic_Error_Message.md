---
title: "[SOLVED] Synaptic Error Message"
date: 2008-08-23
forum: General Help
---

### Post by smith_fan on 2008-08-23
My laptop's Gutsy installation has had a nagging problem with regards to Synaptic which I've not been able to fix.  Whenever I install new packages or even try to apply updates, I get an error referencing msttcorefonts.

Here is some 'Details' text from my latest go-round with Synaptic:
“
ldconfig deferred processing now taking place
Errors were encountered while processing:
  msttcorefonts
E:  Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
“

I have tried fixing broken packages thru Synaptic with no apparent effect. (Though it *did* indicate that there were some problems fixed).  I have uninstalled and purged that package, and then re-installed it and the problem sticks around.

I also tried one guy's sure-fire fix that a search of that error text in Ubuntu forums turned-up.  While I'm happy that it fixed the problem on his system, it did diddley-squat on this 'puter.

I am rather-painfully an absolute noobie to linux.  I haven't come up with a plan for partitioning the hard drive, yet.  And thus I'm not quite ready to install Hardy (with a separate Home partition) which would probably rid myself of this nagging error.  Instead, I'm (very) slowly attempting to fix all the little problems with this installation which my ignorance have created.

Can anyone please help stop the madness?! :shock:

Thanks!,
~D~

---

### Post by Stemp on 2008-08-24
Could you try by the terminal and write the exact error ? 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Elfy on 2008-08-24
Try 

```
sudo apt-get install -f
```

Won't dist-upgrade try and upgrade versions?

---

### Post by smith_fan on 2008-08-24
I have been STRONGLY discouraged from performing an upgrade/update to Hardy and told that doing so is just asking for trouble.

Pixie, here is some Terminal text from when I tried your command:

“...
andale32.exe: No such file or directory 

All done, errors in processing 1 file(s) 
dpkg: error processing msttcorefonts (--configure): 
 subprocess post-installation script returned error exit status 1 
Errors were encountered while processing: 
 msttcorefonts 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
darin@Belinda:~$ 
“
I just haven't invested the time needed to learn all the information required to be able to
understand just exactly what that error message is telling me. (Not sure I'd know where to start to go about doing that, either!  There is just so dang much that I don't understand.  And so much to know!)

Maybe I should just ask you for your thoughts on the best way to dual-boot XP Pro and Hardy Heron on a 74.53 GB SATA drive in this Toshiba laptop.  It came pre-loaded with Vista but only 1 gig of RAM.  (Just enough to make it run like total crap with that bloated piece of...)

I haven't been able to figure-out the best way to partition the hard disc.  I do know that it will have to have a dedicated 'Home' partition.  I am also thinking of 2GB for swap, but am undecided about he rest of it.  I'd like for the Windows installation to be as easily refreshed/reloaded as possible w/o interfering with my user data.

I have also read of several partitioning strategies that call for a dedicated 'usr' partition as well as others.

This should probably be a separate post, but I thought I'd ask how others are doing your hard drives and your methods used for multi-booting.  Currently, I'm using Easy BCD which works well and is well-documented and I planned to continue doing so.

Thanks very much for your input!,
~D~

---

### Post by Elfy on 2008-08-24
You could try -

```
sudo dpkg --configure -a
sudo apt-get remove --purge msttcorefonts
```

As far as upgrading goes I would guess that whoever strongly discouraged it had problems - not everyone does so :) that said I usually reinstall.

If you want to reinstall you don't have to do any partitioning as you can reuse the gutsy partition, if you are looking to get more space then that can be achieved easily enough. I wouldn't bother with seperate /usr, /boot etc. if you weant to have a seperate /home that can make things easier when reinstalling - but I keep all my data seperate anyway now and when I next reinstall shan't be using a seperate /home.

Swap - if you have a need to hibernate then swap=RAM, otherwise I wouldn't have more than 512MB.

---

### Post by mssever on 2008-08-24
> **smith_fan said:**
> I have been STRONGLY discouraged from performing an upgrade/update to Hardy and told that doing so is just asking for trouble.I NEVER reinstall. I've upgraded from Dapper (6.06) all the way to Hardy, with no major problems. Solving any minor problems that might occur is faster than setting up a new install.

> Pixie, here is some Terminal text from when I tried your command:

“...
andale32.exe: No such file or directory 

All done, errors in processing 1 file(s) 
dpkg: error processing msttcorefonts (--configure): 
 subprocess post-installation script returned error exit status 1 
Errors were encountered while processing: 
 msttcorefonts 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
darin@Belinda:~$ 
I don't know why you're getting that error, but I'm guessing that the worst possible consequence of that is that you might not be able to use the Andale font.

---

### Post by hansdown on 2008-08-24
Hi smith_fan. That is an exectable file for microsft.

Have you tried the package in system>administration>synaptic package manager?

Search for msttcorefonts.

---

### Post by smith_fan on 2008-08-24
I believe I tried those commands previously after searching the forums a few weeks back.  Anyway, I ran 'em again, but I still get that damn message in Synaptic.:mad:

The college kid who told me to avoid upgrading implied that a bunch of folks (most of them) had all kinds of headaches after upgrading.  He recommended doing a fresh install of Hardy to avoid them.  I kinda thought that a re-install would stand a good chance of fixing the many little problems that my ignorant blunderings have caused in this Ubuntu installation, too...

Is there a good way to facilitate easy XP re-installs w/o wrecking your settings and user data?  I bought Acronis True Image and Disk Director Suite, but I haven't managed to successfully use the images made with them.  I've read that Paragon Drive Backup is pretty good, too.  I wonder if it's a little more user-friendly?  [FONT="Comic Sans MS"][SIZE="1"]I'm not that bright.[/SIZE][/FONT] :lolflag:

Anybody know?

Thanks!,
~D~

---

### Post by Elfy on 2008-08-25
I assume that none of the fonts are as yet available, you can try to purge the package, but I'm not sure if it will help tbh

```
sudo dpkg --purge msttcorefonts
```if that works try to reinstall it ```
sudo apt-get install msttcorefonts
```

Though to be honest I copied my ms fonts into a directory in home and updated the fonts cache, all that I have left of ms on my pc now :)

If you want to do a clean install it is quick enough if you don't have much configuration to worry about.

Make sure to pick manual when you reach the partition part - highlight the partition that the buntu is on - then edit partition; in the new window there's a drop down Use as menu - pick ext3, there's a mountpoint drop down as well choose / then close and carry on.

---

### Post by smith_fan on 2008-08-25
> **forestpixie said:**
> 
Though to be honest I copied my ms fonts into a directory in home and updated the fonts cache, all that I have left of ms on my pc now :)


What do you mean 'updated the fonts cache'?  That fix I tried for the problem just involved copying all the ttf files from C:\Windows\Fonts.

Please let me know if it's improper ettiquette to post large chunks of text like this, but here's from my Terminal window:

"
darin@Belinda:~$ sudo dpkg --purge msttcorefonts
[sudo] password for darin:
(Reading database ... 169499 files and directories currently installed.)
Removing msttcorefonts ...
W: /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Webdings.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Impact.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: not registered.
dpkg: error processing msttcorefonts (--purge):
 subprocess pre-removal script returned error exit status 1

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
darin@Belinda:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
msttcorefonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up msttcorefonts (2.2) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
darin@Belinda:~$ 

"
If "1 not fully installed or removed.", then just exactly what the heck *IS *it's status?  Partially installed?:confused:

I don't get it, man.

Thanks for your assistance!:),
~D~

---

### Post by Elfy on 2008-08-25
> Try to deselect any proxy settings that you might have made. Use System -> Preferences -> NetworkProxy and make sure that you have Direct connection to the Internet selected. Let me know if this solves the problem.from [http://ubuntuforums.org/showthread.php?t=203521](http://ubuntuforums.org/showthread.php?t=203521)

Really not sure what is going on here, check the proxies and try the apt-get install -f command again. But I am unsure now tbh

_Fonts in home directory_
I copied all my ttf fonts from an old win to a folder I made in /home called .fonts and then ran ```
sudo fc-cache -f -v 
```

---

### Post by dacs83 on 2008-08-26
hi, I have the same problem. The error I get is:

Errors were encountered while processing:  linux-image-2.6.24-19-generic

after upgrade to the new Kernel version.
I read in other post out there it is some grub dependency. I don't have grub installed, instead I installed grub-gfxboot_0.97-5_i386.deb

I didn't go back to grub yet. I'm hoping anyone came up with a solution wich allows me keep my graphic grub. 

Anyone??

PD: I'm very new to linux so don't take this post as an adivice of anything. And sorry for eanglish as I'am not a native speaker.

---

### Post by smith_fan on 2008-08-30
Sorry for the delay with my response.  I upgraded the dist and have been messing with Firefox quite a bit because of the forced version change associated with the browser.

The news is good on almost all fronts. Specifying 'Direct Connection' did eliminate those annoying proxy error messages.  Msttcorefonts is now installed, and at version 2.4 with no hiccups or lingering Synaptic messages. :guitar:  Thanks for your assistance! :)

There's still something kinda hinky about the networking settings, though.  That, a few other error messages, and disc partitioning that won't allow for hibernating plus a still-pending Win XP install pretty much dictate a re-install of Ubuntu in the future.

Can you tell me where documentation files can be located?

Thanks, again, for all your help!

~D~

---

### Post by Elfy on 2008-08-30
Not too sure what you mean by > Can you tell me where documentation files can be located? if you could elaborate a bit I'm sure I'll be able to help you :)

---

### Post by smith_fan on 2008-08-30
Oh, I was afraid that might've been ambiguous.  From a Synaptic window, in the past many times I've noticed in the Details text something along the lines of "configuring docs for ____."  But I dunno where that documentation can be found.  Even the standard GNOME or KDE docs are somewhere that I can't find. :confused:   I do have the regular '? Ubuntu Help Center' that opens when I need it, but I can't find any other instructions or information anywhere.

Now that I'm looking, I can't find any examples (naturally!), but in the past when I've selected new software in Synaptic if they're available I've always grabbed the documentation packages for whatever new software I've installed, too.  A lot of good it's done me, though, because I have no idea where they end up! :mad:

Working one's self off of Windows is pretty frustrating without "the directions!"  Does that make it any clearer, bud?

Thanks, again, for your spot-on assistance, man! Wink

~D~

---

### Post by mssever on 2008-08-31
The -doc packages usually install their documentation in /usr/share/doc/$program. Also, typing ```
man command-or-config-filename
```will bring up the official documentation. There are a number of other documentation types, but often Google is the easiest (aside from the man page; man is short for manual).

---

### Post by smith_fan on 2008-08-31
Beautiful! :D  Thanks very much!

Now for a rather stupid one: upon setting this Ubuntu up, I chose Chicago, IL because that was the closest major choice to where I live and is in my same time zone.  How does one add their specific town that isn't listed in the default location choices?  I find it VERY hard to believe that with such a superior operating system in every other way, that people just have to choose the closest metropolitan area to where they actually live because theirs isn't a listed choice.

But I haven't done any searching about this issue, yet, and I'm pretty sure that this is not the case.

Thanks!,
~D~

---

### Post by mssever on 2008-09-01
> **smith_fan said:**
> Now for a rather stupid one: upon setting this Ubuntu up, I chose Chicago, IL because that was the closest major choice to where I live and is in my same time zone.  How does one add their specific town that isn't listed in the default location choices?  I find it VERY hard to believe that with such a superior operating system in every other way, that people just have to choose the closest metropolitan area to where they actually live because theirs isn't a listed choice.As far as timezones go, if you're in US Central time (and you aren't in Indiana where the timezone rules are very confused), then Chicago is the only available choice. I'm not sure why that is, but it works OK. I'm in Texas--a long way from Chicago--yet setting my timezone to America/Chicago causes me no trouble.

When it comes to the world clock applet on the top panel, the list of cities from which you can choose is much larger.

---

### Post by smith_fan on 2008-09-01
:o  That's just plain strange!  I was thinking that *surely* my brother-in-law was simply wrong about this particular detail or just didn't know what he was talking about in this case.  But, you've just confirmed his assertion.

Thanks for your help!,
~D~

---

