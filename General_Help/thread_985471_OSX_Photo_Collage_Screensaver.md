---
title: "OSX Photo Collage Screensaver"
date: 2008-11-17
forum: General Help
---

### Post by N00b-un-2 on 2008-11-17
the Mac OSX "collage" screen saver is by FAR my favorite screen saver.  I was using the slideshow type screensaver for a while, but after I found the collage screensaver I immediately liked it.  I set OSX to that screen saver and I found a decent clone of the same thing for Windows, but I'm having a hard time finding a similar screensaver for Linux.

---

### Post by M0GEJ on 2009-01-10
Has anyone had any luck finding anything similar? I am guessing that there is nothing like it at the moment but would be happy to be proved wrong...

---

### Post by silvagroup on 2009-08-16
Looks like old post. My wife saw the Mac collage screen saver and now has to have it, and I admit it is very cool. After much searching haven't found anything comparable for Linux.
If some one has a link or a script that will do this some info would be great.
Thanks in advance.

---

### Post by silvagroup on 2009-08-20
WOW, I just can't believe that if M$ and Apple can do this no one in the Linux world can do it, and do it better.:confused:

---

### Post by wankel786 on 2009-10-10
Any update on this one?

---

### Post by silvagroup on 2009-10-10
Nothing! Googling comes up with tons of things for Windows and OSX but nothing for Linux.
The closest thing which is not that close, but it's better than a poke in the eye, is using F-Spot to do a slide show as a screen saver.
Hopefully a good coder will get whiff of the interest in this and do one for Linux. Can't imagine it would be so horribly difficult to do, for me yes but not for a good coder.
Maybe a blast campaign to all the Linux forums will bring it about.
So post the idea away !!!!!

---

### Post by tgalati4 on 2009-10-10
[http://www.jwz.org/webcollage/explain.html](http://www.jwz.org/webcollage/explain.html)

---

### Post by wankel786 on 2009-10-10
> **tgalati4 said:**
> [http://www.jwz.org/webcollage/explain.html](http://www.jwz.org/webcollage/explain.html)

Nice find, too bad it will only display random images from the web :(

---

### Post by tgalati4 on 2009-10-10
The code is open source, so you could tweak it:

[http://www.jwz.org/webcollage/webcollage](http://www.jwz.org/webcollage/webcollage)

For something simpler:

apt-cache search collage
sudo apt-get install metapixel
man metapixel

Run a cron job to create a metapixel collage every hour and place it in your "Pictures" directory.

Select "Pictures" directory screensaver.

Or

Write your own collage screensaver program.  Start by looking at the code for metapixel and the plug-in architecture for xscreensaver.

---

### Post by tgalati4 on 2009-10-11
I just found picturetile which is closer to what you might be looking for:

[http://www.jwz.org/picturetile/](http://www.jwz.org/picturetile/)

There is an f-spot picturetile plugin--but f-spot throws a "not-found" error.

---

### Post by silvagroup on 2009-10-12
Actually webcollage is more what I was looking for, but as wankel786 states it uses random web pictures and that can be very scary.

This would be really great if you could have options, easy options for setting where it gets the pictures.

Very frustrating.:confused:

---

### Post by silvagroup on 2009-10-12
WOW, looking through the code there sure is a lot of code for searching the web for pics.

Seems like it would be easier and safer to set it up to look at local directory in the order of F-Spot and just display those.

Don't have a clue however on how that would be done.

---

### Post by tgalati4 on 2009-10-13
Why don't you send an email to jwz and ask him to code up local collage script?

---

### Post by silvagroup on 2009-10-13
tagalati4 you are a genius, now that IS truly worthy of the Noble Prize. I will do exactly that.
Thanks for the suggestion.

---

### Post by tgalati4 on 2009-10-13
Hey, I just made a speech.  I didn't actually do anything.  I WILL keep the money though.

---

### Post by silvagroup on 2009-10-13
tgalati4 that is very big and humble of you.

Just sent an email.

Looking at all this stuff looks like one should be able to set the directory using the -directory argument but don't know where to do that at.

Will wait to see if there is a response.

---

### Post by tgalati4 on 2009-10-13
My PERL skills are weak, but looking through the code there are a few lines:

```

my $local_magic = 'local-directory';
my $local_dir = undef;

```

So perhaps you can define a local directory, but I don't know how to narrow the scope to just that directory.

---

### Post by silvagroup on 2009-10-13
tgalati4 in /usr/share/xscreensaver/config there is this:

```
<?xml version="1.0" encoding="ISO-8859-1"?>

<screensaver name="webcollage" _label="WebCollage">

  <command arg="-root"/>

  <hgroup>
   <vgroup>
    <number id="delay" type="slider" arg="-delay %"
            _label="Delay between images" _low-label="None" _high-label="30 secs"
            low="0" high="30" default="2"/>

    <number id="timeout" type="slider" arg="-timeout %"
            _label="Network timeout" _low-label="2 secs" _high-label="2 min"
            low="2" high="120" default="30"/>
   </vgroup>
   <vgroup>
    <number id="opacity" type="slider" arg="-opacity %"
            _label="Image opacity" _low-label="Transparent" _high-label="Opaque"
            low="0.1" high="1.0" default="0.85"/>

   <boolean id="showfps" _label="Show frame rate" arg-set="-fps"/>

   </vgroup>
  </hgroup>

<!--
  <string id="filter"  _label="Per-image filter program" arg="-filter %"/>
  <string id="filter2" _label="Overall filter program" arg="-filter2 %"/>
  <file id="dictionary" _label="Dictionary file" arg="-dictionary %"/>
  <file id="dir" _label="Image directory" arg="-directory %"/>
 -->

  <_description>
This makes collages out of random images pulled off of the
World Wide Web.  It finds these images by doing random web searches,
and then extracting images from the returned pages.

WARNING: THE INTERNET SOMETIMES CONTAINS PORNOGRAPHY.

The Internet being what it is, absolutely anything might show up in the
collage including -- quite possibly -- pornography, or even nudity.
Please act accordingly.

See also http://www.jwz.org/webcollage/

Written by Jamie Zawinski; 1999.
  </_description>
</screensaver>
```

Seems like this maybe what is used for setting the variables? maybe?

I tried changing  <command arg="-root"/> 
to 
<command arg="-root" "-directory /home/pics/" 

and nothing happened. 
I am not sure if I did it wrong or this file doesn't actually do anything except take up space.

---

### Post by silvagroup on 2009-10-14
Here is the response from jwz an email and here exactly, is his response:

"--directory"

quick and to the point.

But I tried it in the xml file and did nothing.

Very frustrating.

---

### Post by tgalati4 on 2009-10-14
perl webcollage.pl -directory /home/you/pictures

---

### Post by silvagroup on 2009-10-14
tgalati4, that's in /usr/lib/xscreensaver. Not being a perl programmer jwz
responded to my email asking about "--directory". His recommendation was to drop gnome-screen-saver and use xscreensaver. From what I can gather xscreensaver is more configurable than gnome-screen-saver.
I also found this [http://ubuntuforums.org/showthread.php?t=198809]("http://ubuntuforums.org/showthread.php?t=198809")
That maybe the simpler solution, I am going to try it.
Will post back results.

---

### Post by silvagroup on 2009-10-14
STOP THE PRESSES!!! that link is not necessary, just edit /usr/share/applications/screensavers/webcollage.desktop add -directory /your/directory save file and there you go, webcollage using local files.
Whew, my life is now complete.

---

### Post by tgalati4 on 2009-10-15
I'm glad you got that to work.  Here's jwz's response to gnome-screensaver:

[http://www.jwz.org/xscreensaver/faq.html#gnome-screensaver](http://www.jwz.org/xscreensaver/faq.html#gnome-screensaver)

Item #26.  He ported xscreensaver to Mac Tiger OS X, but he has some concerns about the implementation of gnome-screensaver.  That is a benefit of open source software.  You can disagree with forks and not support them.

But, he has a nice summary of what is available in xscreensaver:

[http://www.jwz.org/xscreensaver/screenshots/](http://www.jwz.org/xscreensaver/screenshots/)

---

### Post by silvagroup on 2009-10-15
Looks like gnome-screen-saver is just a front-end for xscreensaver but without the ability to customise the individual screen savers easily. Kind of ridiculous. why?

That's why getting webcollage settings customised was such a pain with gnome-screen-saver, something which is much easier to do with xscreensaver.

The default install for Ubuntu is gnome-screen-saver, so it's good that this post has some what pierced the capability for customising the individual screen savers.
Obviously not as easily as w/xsreensaver but at least it's doable with gnome-screen-saver.

Maybe some one (much more knowledgeable than I) will take this info and make a How To for screen saver customisations in Ubuntu.

---

### Post by heryatmadja on 2009-11-18
> **silvagroup said:**
> STOP THE PRESSES!!! that link is not necessary, just edit /usr/share/applications/screensavers/webcollage.desktop add -directory /your/directory save file and there you go, webcollage using local files.
Whew, my life is now complete.

Hi silvagroup,

Been trying to follow your instruction, but I can't seem to get it working. I've installed xscreensaver and managed to run the daemon.  When I select Webcollage from the list of screensavers (x not gnome), the images shown are taken from the web.

Here is the change that I made (specifically the Exec tag).

```

[Desktop Entry]
Encoding=UTF-8
Name=WebCollage
Comment=This makes collages out of random images pulled off of the World Wide Web. It finds these images by doing random web searches, and then extracting images from the returned pages. WARNING: THE INTERNET SOMETIMES CONTAINS PORNOGRAPHY. The Internet being what it is, absolutely anything might show up in the collage including -- quite possibly -- pornography, or even nudity. Please act accordingly. See also http://www.jwz.org/webcollage/ Written by Jamie Zawinski; 1999.
TryExec=webcollage
Exec=webcollage -directory /home/heryatmadja/Pictures/Screen-saver
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver;
OnlyShowIn=GNOME;
```

I have restarted the xscreensaver daemon after making the above changes, however I'm still getting web images.  Do you mind sharing with me what you did or help point out where I screwed up? Thanks much.

BTW, I am running on Jaunty.

---

### Post by silvagroup on 2009-11-19
heryatmadja sorry for the slow response, but here''s what you want to do next:
Go to ```
/usr/share/applications/screensavers/webcollage.desktop
```
Open webcollage.desktop (as root) in editor and change Exec=webcollage to look like the line below.
```
Exec=webcollage -root -directory /home/mydirectory/
```
That should do it for you.
Let me know how that works for you.

---

### Post by heryatmadja on 2009-11-23
hi silvagroup,

thanks for the reply.  I followed your suggestion by changing the line as follow

```
Exec=webcollage -root -directory /home/heryatmadja/Pictures/Screen-saver
```

where /home/heryatmadja/Pictures/Screen-saver is the local folder where I store my images. When I run xscreensaver, it's still showing images from the web.  Any idea where else I should check?

Thanks.

---

### Post by silvagroup on 2009-11-28
heryatmadja, sorry not ignoring you just been too busy to check emails.
Try turning off screen saver and restarting it if that doesn't do it reboot and see of that works.

---

### Post by heryatmadja on 2009-11-29
> **silvagroup said:**
> heryatmadja, sorry not ignoring you just been too busy to check emails.
Try turning off screen saver and restarting it if that doesn't do it reboot and see of that works.

No problem silvaroup. I am actually thankful that you are willing to spare the time to help me.  Anyhow, the good news is that the webcollage screen saver works now!!!  The bad news is that restarting it didn't make it work.

Here's how I got it to work, after a light bulb appeared in my head.  While, playing with the settings, I saw a button to do a 'Setting' for the webcollage screen saver.  I clicked on it and click the Advanced button.  I get something like this (the command line is after I added the -directory option).

[IMG]http://img215.imageshack.us/img215/1199/xscreensaverwebcollage.jpg[/IMG]

After clicking OK, long and behold, webcollage is picking pictures from my local directory.  And to satisfy my curiousity, I checked the /usr/share/applications/screensavers/webcollage.desktop file.  The Exec line didn't reflect that what is shown in the image above.  So it seems that the 'configuration' is stored somewhere else.

The 'beauty' of this is that even the gnome screensaver webcollage now picks up images from my local directory.  I still use gnome-screensaver cause the lock screen option in Jaunty seems 'integrated' to it.

So that's how I get it to work.  Thanks for all the help silvagroup.

PS: I hope I am attaching the image the right way.  Tried reading the forum guidelines and couldn't find any 'restrictions' on how to put up image. So...

PPS: Latest method.....

a. I uninstalled xscreensaver
b. Copy /usr/share/applications/screensaver/webcollage.desktop as /usr/share/applications/screensaver/mycollage.desktop (sudo  mode)
c. Edit mycollage.desktop as the following
```

[Desktop Entry]
Encoding=UTF-8
Name=MyCollage
Comment=This makes collages out of random images pulled off of the World Wide Web. It finds these images by doing random web searches, and then extracting images from the returned pages. WARNING: THE INTERNET SOMETIMES CONTAINS PORNOGRAPHY. The Internet being what it is, absolutely anything might show up in the collage including -- quite possibly -- pornography, or even nudity. Please act accordingly. See also http://www.jwz.org/webcollage/ Written by Jamie Zawinski; 1999.
TryExec=webcollage
Exec=webcollage -root -delay 1 -opacity 1 -directory /home/heryatmadja/Pictures/Screen-saver
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver;
OnlyShowIn=GNOME; 
```
d. Open up (Gnome) Screensaver dialog and select MyCollage as my default screensaver
e. That's it!!

---

### Post by silvagroup on 2010-11-15
Well with Maverick this has stopped working !!!!!
Have no clue what is going on as nothing that worked in the past now works.
It still worked with Lucid but as of Maverick no luck.
If any one has any clues any help would be greatly appreciated.
Thanks in advance.

OK forget that, just go to Synaptic search for xscreensaver, and you'll see xscreensaver-webcollage, install and your backup and running.
Only problem is it gives me three in Gnome Screen Saver configuration. Two are the ones using my local folders and one is using the web for gathering pictures.
So if you do this be careful as the web does have some content that you may not want on your screensaver !!!!!!!
Looking through the system can't quit figure out what is happening and why I have three selections ?
And as long as I can use my lcal files rather than web I am fine.
If any one can figure this oout I am sure it would be useful so please post.

---

### Post by JBHoren on 2012-02-01
> **silvagroup said:**
> Well with Maverick this has stopped working !!!!!
Have no clue what is going on as nothing that worked in the past now works.
It still worked with Lucid but as of Maverick no luck.
If any one has any clues any help would be greatly appreciated.
Thanks in advance.

OK forget that, just go to Synaptic search for xscreensaver, and you'll see xscreensaver-webcollage, install and your backup and running.
**[COLOR="Blue"]Only problem is it gives me three in Gnome Screen Saver configuration. Two are the ones using my local folders and one is using the web for gathering pictures.[/COLOR]**
So if you do this be careful as the web does have some content that you may not want on your screensaver !!!!!!!
**[COLOR="Blue"]Looking through the system can't quit figure out what is happening and why I have three selections ?[/COLOR]**
And as long as I can use my lcal files rather than web I am fine.
If any one can figure this oout I am sure it would be useful so please post.

If you look in the available screensavers, you'll find entries for "Pictures Folder", "WebCollage", and "MyCollage". Each entry corresponds to a[FONT="fixedsys"] .desktop [/FONT]configuration file in[FONT="fixedsys"] /usr/share/applications/screensavers[/FONT]

[LIST]
[*][FONT="fixedsys"]personal-slideshow.desktop [/FONT]configures the "Pictures Folder" screensaver
[*][FONT="fixedsys"]webcollage.desktop [/FONT]configures the "Web Collage" screensaver
[*][FONT="fixedsys"]mycollage.desktop [/FONT]configures the "My Collage" screensaver
[/LIST]
It is the last configuration file which you should edit for the directory in which the photos you want displayed are located. It could be /home/<user>/Pictures, or anywhere else on your computer.

Hope this helps!

---

