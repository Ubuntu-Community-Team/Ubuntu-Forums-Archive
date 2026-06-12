---
title: "HOW TO: Install wxMusik"
date: 2005-11-14
forum: General Help
---

### Post by Jamesia on 2005-11-14
Here's a brief little how-to for people wanting to install [wxMusik]("http://musik.berlios.de"). It is a really simple to use, powerful little music player. There are many, many features, just visit their website to see for yourself. I built deb files from the source codes of all the dependences, and rather than package them together, I left them separate so that people can install only the parts they need, rather than overwrite what they have already. In advance, I'll assume that you have GTK2. If not, it's readily available through Synaptic. These are the requirements:

libmusepack 1.0.3 ( not 1.1!) -- included in linked file
libflac (at least1.1) --get in Synaptic
libmac -- included in linked file
fmod sound system (3.74) -- included in linked file
sqlite (at least 2.8.15) -- included in linked file
GTK2 (GTK1 may work, but is not supported) -- should be installed, or get in Synaptic
wxWidgets (at least 2.5.3) -- included in linked file

All of the files needed [are located here]("http://www.jnewto.com/upload/wxmusik.tar").

Once downloaded (it's about 17.0MB in size), open up the terminal and untar it like so:
```
tar -vxf wxmusik.tar
```

Next, you'll want to change to it's directory:
```
cd wxmusik
```

wxMusik supports FLAC, Monkey's Audio, and Musepack formats, so we'll have to install those if you don't have them already. Also, wxMusik is rather picky about what version of Musepack you have, so make sure it is version 1.0.3. It doesn't really matter what version of FLAC you have, so just install whatever is in Synaptic.  We can install Monkey's Audio and Musepack like so:
```
sudo dpkg -i mac-3.99-u4-b4_b4-1_i386.deb
sudo dpkg -i libmusepack-1.0.3_1.0.3-1_i386.deb
```

Now, update your library links by running 
```
sudo ldconfig
```

Next we'll want to install the sound system (FMOD), wxWidgets, and a database system for your musik library (sqlite). 
```
sudo dpkg -i wxgtk-2.6.2_2.6.2-1_i386.deb
sudo dpkg -i sqlite-2.8.16-1_1-1_i386.deb
sudo cp inc/* /usr/include
sudo cp libfmod-3.74.so /usr/lib
sudo ldconfig
```

That should be all of the dependencies. Finally, you can run the file called 'wxMusik' from anywhere that you like. For simplicity, I copied it to a system bin so it can be ran from command line at any time. To do that, simply: 
```
sudo cp wxMusik /usr/bin
```
Now, if you want to run wxMusik, just type it in the terminal.

Finally, if you want a few example playlists to get started with, you can copy the directory 'playlists' into a directory at /home/user_name/.Musik. Fair warning: some of the radio playlists are outdated.


If you want to build wxMusik yourself, download the file at [http://www.jnewto.com/upload/wxMusik-0.4.2.2.tar]("http://www.jnewto.com/upload/wxMusik-0.4.2.2.tar"). Unzip it, switch to the directory called 'crelbuild', and run make then make install. Hopefully that will work. By the way, I think this will negate the need to copy wxMusik to a bin (from the first archive). 
OR, after installing the dependencies, you should be able to configure and build wxMusik from source yourself... just download it from their [website]("http://musik.berlios.de").

***** EDIT    < 11 December 2005 >    ******
Should you receive an error upon opening wxMusik stating that the FMOD sound system failed to load, you simply need to match the sound engine in wxMusik with the one that your system is using. To find out what engine your system is using, go to System --> Preferences --> Multimedia Systems Selector.
Additionally, this version of wxMusik is *supposed* to support ALSA.

Also, I updated wxMusik from version 0.4.2.1 to version 0.4.2.2.

***** EDIT   < 19 December 2005 >    ******
[Duminas]("http://www.ubuntuforums.org/member.php?u=28785") has offered a fix to a problem related to using foreign languages with wxMusik. The error is related to wxWidgets, a dependency of wxMusik, rather than wxMusik itself. The bug (and fix) are related to Japanese specifically, but it may or may not show up languages other than English. The bug report and fix is located [here]("http://developer.berlios.de/bugs/?func=detailbug&bug_id=5912&group_id=925").

---

### Post by duminas on 2005-11-27
Nice HOWTO.
Just thought I'd add something--It'd be wise to NOT run it as root the first time.

I accidentally made that mistake, and as a result, my regular user could not save any configuration changes. Before I saw this HOWTO, I was struggling to get wxMusik working on Ubuntu.

Thanks much--really beats the pants off any other music player I've used. And it's Python. Score~

[size=1]Unfortunately, it is in the wrong place, so it might go missed. :\[/size]

---

### Post by Jamesia on 2005-11-27
Thanks a lot! I like it better than K/Ubuntu various defaults... since I use .mpc and ogg mostly in Windows too. I was curious as to whether my debs worked, so I'm glad to hear they did for you.

About the location, that's my fault... perhaps a generous moderator will remedy that.

---

### Post by Original Brownster on 2005-11-27
Nice howto, thanks. :)

---

### Post by Mattias on 2005-11-27
Hello
Thanks for the deb files..but I can not get it to work. I get "Initialization of FMOD sound system failed" Do you have any tips how to proceed ? 
PS Tried it both on dapper and breezy Ds

---

### Post by duminas on 2005-11-27
```
cp inc/* /usr/include
cp libfmod-3.74.so /usr/lib
ldconfig
```
Note that you need to be superuser for all three of those.
Make sure you didn't miss any of those steps. If you're sure you did those, issue a quick:
```
ls -l /usr/lib/libfmod-3.74.so
```And see if you get a reply. If you do, issue ldconfig again and try to run wxMusik. If you do not, repeat the steps in the first code block and issue ldconfig.

If those fail, try ldconfig with root priviledges (sudo ldconfig), and then run wxMusik as yourself.

---

### Post by Mattias on 2005-11-27
Thank you for your suggestions. I've retried all steps and everything seems fine except when starting wxMusic I get "initialization of FMOD sound system failed"
in a pop up window and no other messages in the terminal window..
I'll guess I'll stick to quodlibet..
/yours

---

### Post by Jamesia on 2005-11-28
For a question on FMOD, I'm afraid you will have to troubleshoot by using their website. ([http://www.fmod.org]("http://www.fmod.org"))

As an initial guess, you may need to play with the sound engine that Ubuntu is using. Off the top of my head, that's located within System -> Preferences -> Multimedia Selector. 

I'm still learning about FMOD myself. Good luck!

---

### Post by Mattias on 2005-11-28
Jamesia, Thank you for setting me on the right track. Changed preferences in multimedia to ESD sink and preferences in wXmusik to ESD and it worked...!!!

thanks

---

### Post by Jamesia on 2005-11-28
Ahh! I thought that might have something to do with it. I'm glad it all worked out!

---

### Post by transactionlogfiller on 2005-11-28
What a great piece of software. Thanks for this howto :)

---

### Post by LazyP on 2005-12-05
a new version of wxMusik has been released with nice bug fixes for Linux. Could you be nice and update your files?

---

### Post by Jamesia on 2005-12-11
I've updated with the new version... It appears that all the dependencies have remained the same. I changed the original post to reflect changes.

---

### Post by kaamos on 2005-12-11
Hello!

Can't get this to run.. Whenever I start the app, it just gives me a debug message. All the debs are installed, and I verified that I had copied the files in the howto. Here's some info:

[http://www.hut.fi/u/alaisi/1.png](http://www.hut.fi/u/alaisi/1.png)
[http://www.hut.fi/u/alaisi/2.png](http://www.hut.fi/u/alaisi/2.png)

Any ideas? Thanks for the howto anyway!

---

### Post by Jamesia on 2005-12-11
I've never seen anything like that! Try compiling it yourself using [http://www.jnewto.com/upload/wxMusik-0.4.2.2.tar.gz](http://www.jnewto.com/upload/wxMusik-0.4.2.2.tar.gz)   
Just change to crelbuild and do make, then make install.

---

### Post by kairu0 on 2005-12-17
You might want to rename the packaged file because it's a tarball (.tar), not a gzipped tarball (.tar.gz).

---

### Post by MetalMusicAddict on 2005-12-17
Thanx a bunch man. I wish This would get in the repos. Everything works but I think some of the commands in the how-to should be changed to add **sudo** in front of them. ie: **sudo ldconfig** and installing the .debs. Except running it for the first time. :)

But thanx again. Ive been waiting to get this going. :)

---

### Post by vvlaw on 2005-12-17
[QUOTE=kaamos]Hello!

Can't get this to run.. Whenever I start the app, it just gives me a debug message. All the debs are installed, and I verified that I had copied the files in the howto. Here's some info:

[http://www.hut.fi/u/alaisi/1.png](http://www.hut.fi/u/alaisi/1.png)
[http://www.hut.fi/u/alaisi/2.png](http://www.hut.fi/u/alaisi/2.png)

Any ideas? Thanks for the howto anyway![/QUOTE]

i had got the same problem :( 

vvlaw@ubuntu:~/tools/player$ wxMusik
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file
addr2line: 'wxMusik': No such file

(wxMusik:10479): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(wxMusik:10479): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
&#24050;&#25918;&#24323;
vvlaw@ubuntu:~/tools/player$

---

### Post by MetalMusicAddict on 2005-12-17
Heres a screenshot. I love the album cover display. Something I wish Rythmbox did. I gotta keep playin with it. Seems a little slow right now.

---

### Post by Kurt Dodrill on 2005-12-18
How do you add an wxMusik icon to the Sound and Video folder?

---

### Post by duminas on 2005-12-18
[QUOTE=kaamos]Hello!

Can't get this to run.. Whenever I start the app, it just gives me a debug message. All the debs are installed, and I verified that I had copied the files in the howto. Here's some info:

[http://www.hut.fi/u/alaisi/1.png](http://www.hut.fi/u/alaisi/1.png)
[http://www.hut.fi/u/alaisi/2.png](http://www.hut.fi/u/alaisi/2.png)

Any ideas? Thanks for the howto anyway![/QUOTE]What language are you using? Issue **locale** in the terminal and find out what the LANG variable is. Or, if you just want to try it this way (make sure these locales are installed!), try executing either of these commands depending on what your locale is:
```
$ LANG=en_US.UTF-8 wxMusik
$ LANG=en_GB.UTF-8 wxMusik
```If that works, it's a bug in his program which I've reported [here](http://developer.berlios.de/bugs/?func=detailbug&bug_id=5912&group_id=925). If you're using a different locale from the one I posted in that thread, feel free to chime in there and tell him.

-----

[QUOTE=Kurt Dodrill]How do you add an wxMusik icon to the Sound and Video folder?[/QUOTE]Assuming you are using Gnome, use smeg. I'm not sure where Breezy sticks it in the menus, but if you want to run it quick just issue **smeg** in the terminal. If it's not installed, issue a
```
$ sudo aptitude install smeg
```in the terminal, and then it should be installed for you.

[size=1]Don't issue the $ as well--I use that to differentiate between lines.[/size]

---

### Post by kairu0 on 2005-12-19
A tip for anyone who uses wxMusik:

It seems to run better when ESD is set as the sound driver in preferences. I used to get false starts when it was set to ALSA.

---

### Post by duminas on 2005-12-19
This is due to wxMusik using FMOD, I'd think.
To my knowledge, only ESD can be used with that?

---

### Post by Breepee on 2005-12-19
Very Nice application. The best there is actually.

Couldn't this be in the repo's?

---

### Post by kairu0 on 2005-12-19
[QUOTE=duminas]This is due to wxMusik using FMOD, I'd think.
To my knowledge, only ESD can be used with that?[/QUOTE]

I have no idea, but that makes sense.

---

### Post by Jamesia on 2005-12-19
Yeah, wxMusik is *supposed* to be compatible with ALSA as of the most recent version, but with all my tinkerings, I haven't been able to get it to work properly. The only working engine seems to be ESD as of yet. I'd really like to be able to use ALSA, so maybe that's foreseeable in the future!

I'm not sure why it hasn't been added to the repos. It's kind of a pain making a deb out of it, so maybe that's why. (?)

PS. I'll change the filename to .tar rather than .tar.gz and the commands for the tutorial. I always run a root terminal, so I forget to add 'sudo'.

---

### Post by Breepee on 2005-12-20
Now that there is a deb, wouldn't it be easy to add it?

---

### Post by MetalMusicAddict on 2005-12-20
[QUOTE=Breepee]Now that there is a deb, wouldn't it be easy to add it?[/QUOTE]
Nothing aginst Jamesia but maybe they will make their own official one. Jamesia, the GUI is a little slow for me. Meaning the GUI is slow to respond to clicks. Maybe something in the compile? Im pretty sure I have everything installed right. I have the win version on the same machine and it works faster so I dont know what the problem is. :???:

---

### Post by duminas on 2005-12-20
That happens for me too, on occasion.
It seems that wxMusik is slowest when I'm browsing through my Japanese files, taking a couple seconds to resopond to me double-clicking a song (I keep it in Library). It's so sporadic, though, as sometimes it's blazing fast, other times it's slow as molasses.

Ah, well. It bests Quod Libet, I think, so I can't complain.

[size=1]I blame Breezy. XD[/size]

---

### Post by MetalMusicAddict on 2005-12-20
Actually, I have a ***LARGE*** music collection. 12k or so songs. Maybe thats part of it on linux. Only thing is I have contrast with the win version. I dont get a lag there.

---

### Post by kairu0 on 2005-12-20
[QUOTE=Jamesia]I'm not sure why it hasn't been added to the repos. It's kind of a pain making a deb out of it, so maybe that's why. (?)[/QUOTE]

On a similar note, the version of quodlibet (another python-based GTK music player) in the repos is grossly obsolete. I think we've uncovered a George W. Bush/NSA conspiracy to prevent the release of python-based-Linux-audio-technology.

---

### Post by Jamesia on 2005-12-20
MetalMusicAddict: I've heard that really large libraries are slow to run on sqlite databases. I wouldn't know for sure, but I bet that has something to do with it. 

kairu0: Now, now, I have enough headaches thinking about Bush... I don't need more :)

For anyone else:
I'm sure that after you install the dependencies, you should be able to download the wxMusik source and build that like the directions say. The biggest hangup on the whole process is simply finding the dependencies, since the Musepack and FMOD versions wxMusik requires are older than the current versions... most websites don't even post them anymore. I had to search long and hard for the right ones!

At any rate, there is one part of building wxMusik that I should warn people about. When you run the command with cmake, and all the configuration options come up, make sure that you select to have shared libraries enabled. The default selection is "No" ... but it needs to be "Yes". Other than that, I think it is ok.

I will copy the compile directions here to show you what I mean:
> #  unarchive the source
# cd wxMusik-0.4.2.0/
# the wxMusik cmake scripts allow a out-of source build, so we create a subdirectory for the compiled files
# mkdir crelbuild
# cd crelbuild
# execute " ccmake -DCMAKE_BUILD_TYPE:STRING=RelWithDebInfo .. ", and assure all the libraries listed above are found. If not you can disable the use of MAC,MPC or FLAC libs now.
# while inside "ccmake", you can set CMAKE_BUILD_TYPE to RelWithDebInfo,Release (or Debug if you want a Debug Build) and CMAKE_INSTALL_PREFIX
# You can now choose which wxwidgets lib should be used, unicode version or not and or if a wxwidgets should be statically linked or not.

***** At this point, make sure wxwidgets lib is shared!! *******

# press "c" to configure(maybe several times, until the [g] option apears), then "g" to generate the makefile
# run make
# if all is right, an executable named "wxMusik" will be generated.
# run ./wxMusik in the current dir to try it out
# do a 'make install' to install binary and data to CMAKE_INSTALL_PREFIX. All languages will be installed
# copy the example playlists and radio channels from wxMusik-0.4.2.0/contrib/playlists to ~/.Musik/playlists
Doing everything else like these instructions say should be ok.


Building wxWidgets was easy, but it takes a little time. So I bet duminas (who has trouble with Japanese characters) might be able to build that dependency himself to fix the issue... rather than use the one I provided. That might help people that have other languages default (if they're having trouble).

---

### Post by Talldave2002 on 2005-12-28
Thanks for the Great How To. this has to be the best music player I have seen.

---

### Post by irish rebel on 2005-12-31
great package , ok here is the deal though when all needed files are installed I just application menu  and in command [after add new program] I just pointed it to the run file and it works .However what are the differances between it and rhythmbox,Wxmusik looks alot slicker on the website.

---

### Post by Jamesia on 2005-12-31
It comes down to a matter of preference. Also, I don't think rhythmbox supports dynamic playlists and a lot of the sound features that wxMusik does. Replaygain, fades, and MPC support in wxMusik are one of a kind, and sound is just plain better in wxMusik. I think the layout for your library is much more intuitive in wxMusik. I think rhythmbox can use a database to organize files, so in that respect I think they're the same. This is probably beside the point, but I don't think you should get too hung up on which one is best... an argument like that about any similar programs always comes down to what you prefer. That's why most of my sentences in this reply contain "I think..." :)
Thanks for the try out though! I'm glad to hear it's running for you!

---

### Post by pkaeding on 2006-01-02
[QUOTE=duminas]
Assuming you are using Gnome, use smeg. I'm not sure where Breezy sticks it in the menus, but if you want to run it quick just issue **smeg** in the terminal. If it's not installed, issue a
```
$ sudo aptitude install smeg
```in the terminal, and then it should be installed for you.

[size=1]Don't issue the $ as well--I use that to differentiate between lines.[/size][/QUOTE]

I am having trouble with this.  Whenever I start wxMusik from the menu or from a launcher on the panel, I get the following error:

```
Initialization of FMOD sound system failed.
```

and the sound doesn't play.  If I start wxMusik from a terminal or the command line applet in my panel, it works fine.

Does anyone have any ideas?

---

