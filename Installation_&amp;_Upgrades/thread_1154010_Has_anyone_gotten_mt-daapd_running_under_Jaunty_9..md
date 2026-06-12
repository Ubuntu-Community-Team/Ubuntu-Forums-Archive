---
title: "Has anyone gotten mt-daapd running under Jaunty 9.04 server?"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by wesg on 2009-05-09
I installed Jaunty 9.04 server right after it came out, and have been trying to get mt-daapd running every since. I tried from the repository, and compiling from source, but nothing has worked. Most recently, I found a segfault when I compiled. 

Has anyone had it running under 9.04?

---

### Post by alek66 on 2009-05-12
I could install it under 9.04 desktop its working  like a swiss watch

does anyone know if theres a way if I use Itunes to modify the ratings on the firefly mp3???

---

### Post by bgturk on 2009-05-22
I am having trouble with it too. 
I just downloaded it, and tried to run it by typing:

/etc/init.d/mt-daapd start

which seemed to go OK. But I had no luck connecting to it.

Checking, the daemon does not appear in the list of services (ps aux). 

I ran dmesg and it seems like it is getting a segmentation fault:

[104807.764671] mt-daapd[3399]: segfault at 0 ip b73854d2 sp b6f22230 error 4 in libdbus-1.so.3.4.0[b735f000+36000]

---

### Post by gammb on 2009-05-22
Inexperienced Jaunty desk user with mt-daapd v09r1696 has same symptoms.  mt-daapd fails with these tidbits left in syslog.
```
Error loading plugin /usr/lib/mt-daapd/plugins/ssc-ffmpeg.so: /usr/lib/mt-daapd/plugins/ssc-ffmpeg.so: undefined symbol: avcodec_decode_audio
Error loading plugin /usr/lib/mt-daapd/plugins/ssc-script.so: plugin declined to load
kernel: [87326.528121] mt-daapd[29877]: segfault at 4 ip b74886b6 sp b70201e8 error 6 in libdbus-1.so.3.4.0[b7463000+36000]
```
...and these jewels in dmesg...
```
mt-daapd[29877]: segfault at 4 ip b74886b6 sp b70201e8 error 6 in libdbus-1.so.3.4.0[b7463000+36000]
mt-daapd[30218]: segfault at 0 ip b74484d2 sp bf940a50 error 4 in libdbus-1.so.3.4.0[b7422000+36000]
```
My sound devices are all set to [AutoDetect] and therein the bottom ALSA, OSS, & Pulse entries all test OK.
Appreciate any guidance/help with mt-daapd
My goal is to have a Roku soundbridge see smart playlists "shared" out from my Jaunty desktop.
Back when I had a windoz box running iTunes, I used Rhythmbox 11.  Hardy has Rhythmbox 12 which (1) gets stuck on whole albums while shuffling through my smart playlist, and (2) although Roku can see the Rhythmbox library, playlists are not found.

---

### Post by maquina on 2009-05-23
Hi,

I had the same problem. If i stop the avahi-daemon, it works:

sudo /etc/init.d/avahi-daemon stop

Then restart mt-daapd

sudo /etc/init.d/mt-daapd start

and you should be good to go

---

### Post by gammb on 2009-05-23
Thanks, killing off the avahi-daemon (without knowing anything about what it does) got mt-daapd up and running, and I was able to open the web gui to configure Firefly.  The server seems happy and is now supposedly serving up some 27K songs.
Sadly, both iTunes and Roku remain unable to discover it.

On FireFly Wiki's Troubleshooting page, I learned you can start mt-daapd with the -m option to disable it's mDNS server so it won't conflict with avahi's.  Since that sounds cleaner, I tried it.
```
sudo vi /etc/init.d/mt-daapd #add a new line just below the DAEMON declaration
     DAEMON=/usr/sbin/mt-daapd
     DAEMON_OPTS=-m
```
(DAEMON_OPTS is an undeclared variable used in the star section)
...and the init will now execute 'mt-daapd -m'

Next, I'm told one must edit /etc/avahi/avahi-daemon.conf so it will publish "DAAP" and "RSP" so the Bonjour protocol (used by iTunes to find servers) will discover us.
```
sudo vi /etc/avahi/avahi-daemon.conf # append to [publish] section
publish-daap=yes
publish-rsp=yes
```

Sounds great, doesn't it.  Unfortunately, that is apparently NOT the right syntax and avahi-daemon dies upon startup.

....and, still, neither iTunes nor Roku either one yet see my server or it's playlists.  :-(

---

### Post by gammb on 2009-05-23
After an extensive search of the forum, I happened upon the solution which I unfortunately dismissed before I thought to note the author so I could provide proper attribution.
Nonetheless, I am pleased to say my Roku is now happily playing random selections from a Firefly smart-play-list on my Jaunty desktop !

This, I believe, is the succinct HowTo for Firefly on Jaunty....

1) Use Synaptic Package Manager to load "mt-daapd"
2) Edit /etc/init.d/mt-daapd to add the "DAEMON_OPT=-m" assignment
3) Create file /etc/avahi/services/daap.service containing
```
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<!-- $Id: ssh.service 1391 2007-02-07 11:54:54Z lennart $ -->
<!-- See avahi.service(5) for more information about this configuration file -->

<service-group>
  <name replace-wildcards="yes">%h</name>

  <service>
    <type>_daap._tcp</type>
    <port>3689</port>
  </service>
  
  <service>
    <type>_rsp._tcp</type>
    <port>3689</port>
  </service>

</service-group>
```
NOTE: If you happen to be tailing syslog when you write the file, you'll see avahi-daemon find it and begin publishing daap.
4) Start the mt-daapd ('/etc/init.d/mt-daapd start')
5) web-browser [http://localhost:3689/](http://localhost:3689/) to configure Firefly.  Let the initial scan run until it has found all your tunes, then create your smart playlist(s).
6) Restart your Roku Soundbridge and select a playlist.
7) Pour a celebratory glass of some of Kentucky's finest, kick back, and enjoy some really loud music. (Ok, I suppose step 7 is optional)

---

### Post by maquina on 2009-05-26
Hi!

this worked for me thank you!

---

### Post by conholster on 2009-05-27
Thank you very much gammb :D Doing step 7 now, except I'm drinking coffee :D

---

### Post by SagaciousB on 2009-06-02
Thank you so much for posting the solution! I haven't been able to use my Roku since upgrading to Jaunty. I finally have music in the living room again.

---

### Post by Cirion on 2009-06-07
I have a linux box serving music to the whole household, amongst others.
Before upgrading to Ubuntu 9.04 I had a perfectly working mt-daapd installation on the previous Ubuntu version.  My music library poped up nicely in iTunes, and played like a charm, even though all my music files are .flac.
After the upgrading to 9.04, the mt-daap service stopped showing in iTunes.  I installed Songbird media player on my mac, same problem.  After going through the steps mentioned in this thread, the mt-daapd service finally showed in both iTunes and Songbird again.  My only problem now is that when I'm clicking on the the mt-daapd service in iTunes it just dissappears, and nothing happens.  After a while it starts showing in the shared list again, but the same happens again...  In Songbird it behaves just fine, and plays like a charm.
Any ideas anyone?

---

### Post by Cirion on 2009-06-07
Hmm, I think I found the solution for my problem, but an other one occured...
I found that my library not appearing in iTunes was related to me upgrading to iTunes 8.1.

By adding a few extra lines to /etc/avahi/services/daap.service, the mt-daapd service showed in iTunes again, an when selecting it, iTunes downloads the music list.

```
<service>
  <type>_daap._tcp</type>
  <port>3689</port>
[COLOR="DarkGreen"]  <txt-record>txtvers=1</txt-record>
  <txt-record>iTSh Version=131073</txt-record>
  <txt-record>Version=196610</txt-record>[/COLOR]
</service>
```

My problem now, is that iTunes won't play anything.  I'm suspecting that mt-daapd are serving the music files in a format that iTunes don't like...

---

### Post by Cirion on 2009-06-07
My system log shows me this:

mt-daapd[7793]: Error loading plugin /usr/lib/mt-daapd/plugins/ssc-script.so: plugin declined to load 
mt-daapd[7793]: Error loading plugin /usr/lib/mt-daapd/plugins/ssc-ffmpeg.so: /usr/lib/mt-daapd/plugins/ssc-ffmpeg.so: undefined symbol: avcodec_decode_audio 

Makes sense though, cuz if I've gotten it right the ssc-script.so plugin is needed by mt-daapd to transcode flac files (amongst others) to wav files that iTunes can play.

After googling this I found that this was a known issue after upgrading ubuntu:
[https://bugs.launchpad.net/ubuntu/+source/mt-daapd/+bug/378390](https://bugs.launchpad.net/ubuntu/+source/mt-daapd/+bug/378390)
Seems like there is no salvation to be found yet...

---

### Post by Cirion on 2009-06-11
It's all working again!  scnaifeh@launchpad have created a fix for the ssc-ffmpeg plugin, and posted a temporary fix for it at: [https://bugs.launchpad.net/ubuntu/+source/mt-daapd/+bug/378390](https://bugs.launchpad.net/ubuntu/+source/mt-daapd/+bug/378390)

---

### Post by wesg on 2009-06-11
My copy of mt-daapd is working now, but only because I'm running the command mt-daapd -m without using the daemon system. Fortunately this server is always on. 

If you can't get it to run, try the command ```
sudo mt-daapd -m
``` and see what happens.

---

### Post by donbroadband on 2009-06-18
I have tried all the solutions proposed in this thread but I cannot get MT-daapd to run. When I initially install the package via Package manager it starts ok and serves my media player (Roku M1001) excellently. If I then switch the system off and restart Ubuntu I cannot adress Mt-daapd via the WEB interface and the daemon is not running. Firefly runs great under windows XP without any of these problems BUT I want to switch to LINUX. I notice that  the originator of Mt-Daapd Ron Peddle has never commented about MT-daapd in this forum despite the problems everyone seems to be having with this product. Should I just give up and regress to Ubuntu 8.04? In desperation I have tried to install MediaTomb but that behaves in exactly the same way - works OK when initially installed but after a restart it can no longer be accessed via the Web Interface, or be seen by  the media players

---

### Post by donbroadband on 2009-06-19
A quick update. I decided to install Ubuntu 8.04 on the same hardware that 9.04 had NOT worked on. I could not get 8.04 to install from the CD so I had to carry out an XP PRO build the install 8.04 under windows.  MT-DAAPD 1696 and MEDIATomb are now both installed and working perfectly together/concurrently. No hang ups failing to start or anything - so I guess the problem must exist with 9.04?

I am puzzled as to why 8.04 would not install in its own right, it would go part way through the install and then say something about HDD block errors, yet xp had no problems nor did Ubuntu under XP.

---

### Post by mashedbear on 2009-06-27
> **gammb said:**
> After an extensive search of the forum, I happened upon the solution which I unfortunately dismissed before I thought to note the author so I could provide proper attribution.
Nonetheless, I am pleased to say my Roku is now happily playing random selections from a Firefly smart-play-list on my Jaunty desktop !

This, I believe, is the succinct HowTo for Firefly on Jaunty....

1) Use Synaptic Package Manager to load "mt-daapd"
2) Edit /etc/init.d/mt-daapd to add the "DAEMON_OPT=-m" assignment
3) Create file /etc/avahi/services/daap.service containing
```
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<!-- $Id: ssh.service 1391 2007-02-07 11:54:54Z lennart $ -->
<!-- See avahi.service(5) for more information about this configuration file -->

<service-group>
  <name replace-wildcards="yes">%h</name>

  <service>
    <type>_daap._tcp</type>
    <port>3689</port>
  </service>
  
  <service>
    <type>_rsp._tcp</type>
    <port>3689</port>
  </service>

</service-group>
```
NOTE: If you happen to be tailing syslog when you write the file, you'll see avahi-daemon find it and begin publishing daap.
4) Start the mt-daapd ('/etc/init.d/mt-daapd start')
5) web-browser [http://localhost:3689/](http://localhost:3689/) to configure Firefly.  Let the initial scan run until it has found all your tunes, then create your smart playlist(s).
6) Restart your Roku Soundbridge and select a playlist.
7) Pour a celebratory glass of some of Kentucky's finest, kick back, and enjoy some really loud music. (Ok, I suppose step 7 is optional)

I have just upgraded to 9.04 and was not aware of this bug. This fix has worked for me - thank you!

Only one minor cosmetic thing left - for some reason the web ui [http://localhost:3689/config.html](http://localhost:3689/config.html) can't edit the mt-daapd.conf (well it says it can but the changes aren't saved). And the name of the server is my local host and not the servername which is actually in mt-daapd.conf . Anyone know how to fix this?.

---

### Post by hradek on 2009-08-05
> **gammb said:**
> After an extensive search of the forum, I happened upon the solution which I unfortunately dismissed before I thought to note the author so I could provide proper attribution.
Nonetheless, I am pleased to say my Roku is now happily playing random selections from a Firefly smart-play-list on my Jaunty desktop !

This, I believe, is the succinct HowTo for Firefly on Jaunty....

1) Use Synaptic Package Manager to load "mt-daapd"
2) Edit /etc/init.d/mt-daapd to add the "DAEMON_OPT=-m" assignment
3) Create file /etc/avahi/services/daap.service containing
```
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<!-- $Id: ssh.service 1391 2007-02-07 11:54:54Z lennart $ -->
<!-- See avahi.service(5) for more information about this configuration file -->

<service-group>
  <name replace-wildcards="yes">%h</name>

  <service>
    <type>_daap._tcp</type>
    <port>3689</port>
  </service>
  
  <service>
    <type>_rsp._tcp</type>
    <port>3689</port>
  </service>

</service-group>
```
NOTE: If you happen to be tailing syslog when you write the file, you'll see avahi-daemon find it and begin publishing daap.
4) Start the mt-daapd ('/etc/init.d/mt-daapd start')
5) web-browser [http://localhost:3689/](http://localhost:3689/) to configure Firefly.  Let the initial scan run until it has found all your tunes, then create your smart playlist(s).
6) Restart your Roku Soundbridge and select a playlist.
7) Pour a celebratory glass of some of Kentucky's finest, kick back, and enjoy some really loud music. (Ok, I suppose step 7 is optional)

Before doing this, make sure you set proper permissions to the folders in your shared music folder. I had a peculiar situation where only a few albums showed up. Running a chmod on all the files with option -R fixed the problem.

---

### Post by elproducto on 2009-08-06
I was able to start MT-DAAPD via the CLI:

```
sudo /etc/init.d/mt-daapd start
```But it does start automatically at boot.  

I entered the command sudo update-rc.d mt-daapd defaults.  I get the following response:

```
update-rc.d: warning: /etc/init.d/mt-daapd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System startup links for /etc/init.d/mt-daapd already exist.
```Should I be concenered with the "missing LSB information". Is there somewhere else I can look for errors pertaining to this program. I have looked in the log view and can't find "mt-daapd" in any section until after I launch the program manually. BTW I am using Jaunty desktop and svn-1696 of Firefly.

Thanks for any help

---

### Post by ntginson on 2009-09-12
I hope someone can shed light to my concern. I am a recent convert of Ubuntu and am now using Jaunty on my desktop that used to store/stream  media to my home network under windows xp. I followed the steps in installing mt-daapd/firefly at:

[http://www.ubuntugeek.com/howto-setup-itunes-compatible-media-server-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-itunes-compatible-media-server-in-ubuntu.html)

and can successfully log to its web ui. My dilemma is that I dont know where the /home/media/music is located, or how to make a folder for all my music collection (48.3gigs worth) so that it will show up in mt-daapd/firefly.

Thanks for the assist

Nathan

---

### Post by piemonkey on 2009-09-29
> **ntginson said:**
> My dilemma is that I dont know where the /home/media/music is located, or how to make a folder for all my music collection (48.3gigs worth) so that it will show up in mt-daapd/firefly.

I'm not sure what you mean, /home/media/music is a location...

If you haven't figured this out by now (as it's been 2 weeks) then it's worth checking out [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount) It should explain some of how ubuntu treats file and directory locations as opposed to windows (you'll find no C:\ here...)

---

