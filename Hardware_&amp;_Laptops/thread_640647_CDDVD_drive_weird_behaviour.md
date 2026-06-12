---
title: "CD/DVD drive weird behaviour"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by Korrontean on 2007-12-14
Hi!

I'm having trouble with the CD/DVD drive in my laptop. When I insert a movie DVD, this is the message I ALWAYS get (see attachment).

Then, some films will work opening them with VLC but most of them will not. No criteria that I could make out.

Any suggestions of what I can do?

---

### Post by Nano Geek on 2007-12-20
Could you post your **/etc/fstab**?

---

### Post by LaRoza on 2007-12-20
> **Korrontean said:**
> Hi!

I'm having trouble with the CD/DVD drive in my laptop. When I insert a movie DVD, this is the message I ALWAYS get (see attachment).

Then, some films will work opening them with VLC but most of them will not. No criteria that I could make out.

Any suggestions of what I can do?

What laptop do you have?

Try:

```

sudo mkdir /media/cdrom0

```

---

### Post by Korrontean on 2007-12-20
asjdfwejqrfjcvm msz34rq33: can you please explain me how to post my /etc/fstab?

First thing I tried:

```
jon@jonatubuntustudiojajaja:~$ /etc/fstab
bash: /etc/fstab: Permission denied
```

Then I moved to the etc directory, this is what I tried:

```
jon@jonatubuntustudiojajaja://etc$ cd fstab
bash: cd: fstab: Not a directory
```

```
jon@jonatubuntustudiojajaja://etc$ fstab
bash: fstab: command not found

```

The dir in my etc directory is the following:

```
jon@jonatubuntustudiojajaja://etc$ dir
acpi                    gxine                passwd
adduser.conf            hal                  passwd-
adjtime                 hdparm.conf          pcmcia
aliases                 host.conf            perl
alternatives            hostname             php5
anacrontab              hosts                pnm2ppa.conf
apache2                 hotplug              popularity-contest.conf
apm                     hp                   power
apt                     iftab                ppp
ardour2                 inetd.conf           pppstatus
at.deny                 init.d               printcap
avahi                   initramfs-tools      profile
bash.bashrc             inputrc              protocols
bash_command_not_found  iproute2             pulse
bash_completion         issue                python
bash_completion.d       issue.net            python2.4
beagle                  j2se                 python2.5
belocs                  java                 qt3
blkid.tab               java-1.5.0-sun       rc0.d
blkid.tab.old           java-6-sun           rc1.d
bluetooth               jvm                  rc2.d
bonobo-activation       jvm.d                rc3.d
brlapi.key              kde3                 rc4.d
brltty                  kernel-img.conf      rc5.d
brltty.conf             laptop-mode          rc6.d
ca-certificates.conf    ldap                 rc.local
calendar                ld.so.cache          rcS.d
chatscripts             ld.so.conf           readahead
console-setup           ld.so.conf.d         resolvconf
console-tools           ld.so.hwcappkgs      resolv.conf
cron.d                  lftp.conf            rmt
cron.daily              libao.conf           rpc
cron.hourly             libgda               samba
cron.monthly            libpaper.d           sane.d
crontab                 locale.alias         scim
cron.weekly             localtime            screenrc
cups                    logcheck             scrollkeeper.conf
dbus-1                  login.defs           securetty
debconf.conf            logrotate.conf       security
debian_version          logrotate.d          services
default                 lsb-base             sgml
defoma                  lsb-base-logging.sh  shadow
deluser.conf            lsb-release          shadow-
devfs                   ltrace.conf          shells
dhcp3                   magic                skel
dictionaries-common     mailcap              sound
dpkg                    mailcap.order        ssh
emacs                   manpath.config       ssl
environment             mediaprm             sudoers
esound                  menu-methods         synfig
event.d                 mime.types           sysctl.conf
fdmount.conf            mke2fs.conf          syslog.conf
ffserver.conf           modprobe.d           terminfo
firefox                 modules              texdoctk
fonts                   modutils             texmf
foomatic                mono                 timezone
fstab                   motd                 timidity
fstab~                  motd.tail            ucf.conf
fstab.old               mtab                 udev
fstab.pre-uuid          mysql                uniconf.conf
gaim                    nanorc               updatedb.conf
gamin                   ndiswrapper          update-notifier
gconf                   Net                  usplash.conf
gdm                     netscsid.conf        vim
gimp                    network              vnc.conf
gnome                   NetworkManager       w3m
gnome-app-install       networks             wgetrc
gnome-system-tools      nsswitch.conf        wifi-radar.conf
gnome-vfs-2.0           ntp.conf             wired
gnome-vfs-mime-magic    ODBCDataSources      wodim.conf
gram.yafray             odbc.ini             wordpress
gre.d                   odbcinst.ini         wpa_supplicant
groff                   openalrc             wvdial.conf
group                   openoffice           X11
group-                  opt                  xdg
gshadow                 pam.conf             xml
gshadow-                pam.d                zsh_command_not_found
gtk                     pango
gtk-2.0                 papersize
```

I'm sorry :oops: it's obvious I have no idea of what I'm doing...

LaRoza: I have an Aspire 3500, I've been trying to figure out what kind of DVDRW drive I have but couldn't find the info.........

I'm at the library and I only have a CD with me (I have no problem to mount CDs, only DVDs), so I can't try this command with a DVD at the moment. I'll try as soon as I get back home.

THANK YOU BOTH!!! :)

---

### Post by Korrontean on 2007-12-20
I guess I had to "gedit" the file???

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d9aaaa8c-9da0-4838-a389-425a84073536 /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3	/media/Archive	ext3    auto,user,rw	0       2
#UUID=822a90c9-fcd0-43b6-866e-b7c565d1ee3a
# /dev/sda1
UUID=44d0f0e3-cf9a-48bb-8592-86a9e6458417 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by Korrontean on 2007-12-20
I have no idea if it's relevant, but when I gedit the file I get this message in the terminal:

```
jon@jonatubuntustudiojajaja://etc$ gedit fstab

(gedit:6253): Gnome-WARNING **: invalid gnome config path '=/section/key'


(gedit:6253): GLib-GObject-WARNING **: gsignal.c:1019: unable to lookup signal "show" of unloaded type `GtkMessageDialog'

(gedit:6253): GLib-GObject-CRITICAL **: g_signal_add_emission_hook: assertion `signal_id > 0' failed
```

---

### Post by Nano Geek on 2007-12-20
Hmm. Nothing looks strange in your fstab file, and I don't think those errors have to do with your problem.

Have you tried LaRoza's suggestion yet?

---

### Post by Korrontean on 2007-12-20
Not yet, asjdfwejqrfjcvm msz34rq33, I'll try as soon as I get home and have a DVD at hand.

Thanks!!! :)

---

### Post by Korrontean on 2007-12-21
:-s :-s :-s ooorrrrrggggghhhhhhhhhh it's getting more and more confusing. I'll try to explain step by step.

In England, where I'm studying, everytime I inserted a film DVD in my laptop I had this message saying it was impossible to mount the disc. Then, when trying to open the disc with VLC, sometimes they worked, sometimes not.

Now I'm on holidays back home, in the Basque Country (just in case you were wondering, same PAL zone as England). I insert film DVDs and I get two different responses (never the "unable to mount" message again).

1.- Either the disc works with no problem

2.- Or I get a message saying the DVD is encripted and asking ¿are you trying to read the DVD without "libdvdcss" ? (I'm translating from Basque, as this is the language my Ubuntu speaks). Obviously I have the libdvdcss package installed.

I know this is not the place to talk about my feelings :roll: but I feel:

1.- Totally confused, and I'm afraid the people trying to help me will think I'm posting wrong information (like "it doesn't make sense") :---)

2.- Afraid I won't be able to play DVDs normally again.......... :cry:

So......thank you for your patience.............and I hope somebody can make sense of what is going on! [-o<

---

### Post by Nano Geek on 2007-12-21
Try running this and see if it helps. ```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by Korrontean on 2007-12-21
Thanks asjdfwejqrfjcvm msz34rq33, I won't be able to try until Monday, when the library opens again. Have a nice weekend. :-)

---

### Post by Nano Geek on 2007-12-21
You too, and merry Christmas.

---

### Post by LaRoza on 2007-12-21
> **Korrontean said:**
> 
Now I'm on holidays back home, in the Basque Country (just in case you were wondering, same PAL zone as England). I insert film DVDs and I get two different responses (never the "unable to mount" message again).

1.- Either the disc works with no problem

2.- Or I get a message saying the DVD is encripted and asking ¿are you trying to read the DVD without "libdvdcss" ? (I'm translating from Basque, as this is the language my Ubuntu speaks). Obviously I have the libdvdcss package installed.

I know this is not the place to talk about my feelings :roll: but I feel:

1.- Totally confused, and I'm afraid the people trying to help me will think I'm posting wrong information (like "it doesn't make sense") :---)

2.- Afraid I won't be able to play DVDs normally again.......... :cry:

So......thank you for your patience.............and I hope somebody can make sense of what is going on! [-o<

For the DVD's: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I don't speak euskara, although I am partly of that heritage. (See my name)

---

### Post by Korrontean on 2008-01-16
Hi!

I haven't been able to take care of the problem for a few weeks...........now I'm back, tried all the solutions you suggested, still can't find a solution. Some DVDs just won't work (same region as If I try to open them with Totem the message I get is (something similar, as I get it in Basque):

```
Iturburua enkriptatuta dagoela dirudi eta ezin da irakurri. Enkriptatutako DVDa erreproduzitzen saiatzen ari zara libdvdcss gabe?.

The source seems to be encripted and cannot be read. Are you trying to read an encripted DVD without libdvdcss?
```

If I try to open it with VLC, I don't get any message. It just won't work.

If I try open it with gxine, it says:

```
Read error from:
Error reading NAV packet.
```

Thank you very much for your help.....

---

### Post by Korrontean on 2008-01-16
Two updates: I installed and tried Kaffeine.......the outcome is this message:
> 
The source can't be read.
Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (Error reading NAV packet.)

I found this in another thread for a very similar problem but I couldn't find the file to edit:

> 
Quote:
Originally Posted by wxm505

Then I tired it with Totem. The player closed unexpectly.

error message pop up:

An error occured
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

I did installed the libdvdcss.
So I do not know how to solve it out
Any help???
Cheers
Try to open the totem.conf file in your /home/.gnome/ directory, there will be a line quoted, referring to libdvdcss2, unquote this line

Sorry for my english :P

THANKS!!!

---

### Post by Korrontean on 2008-01-16
I've finally found totem.conf..........any suggestion on how to change it? I don't see any reference to libdvdcss2 even if it IS installed.......
> 
#
# xine config file
#
.version:2

# Entries which are still set to their default values are commented out.
# Remove the '#' at the beginning of the line, if you want to change them.

# OSD eta azpitituluetan erabiliko den paleta (aurreko-ertza-atzeko koloreak)
# { white-black-transparent  white-none-transparent  white-none-translucid  yellow-black-transparent }, default: 0
#ui.osd.text_palette:white-black-transparent

# hardware nahasleari aldaketen berri eman
# bool, default: 1
#audio.alsa_hw_mixer:1

# audio driver to use
# string, default: auto
#audio.driver:auto

# A/52 bitarte dinamiko konpresioa
# bool, default: 0
#audio.a52.dynamic_range:0

# downmix audio to 2 channel surround stereo
# bool, default: 0
#audio.a52.surround_downmix:0

# A/52 bolumena
# [0..200], default: 100
#audio.a52.level:100

# mono irteerarako erabiliko den gailua
# string, default: default
#audio.device.alsa_default_device:default

# Estereo irteerak erabiltzen duen gailua
# string, default: plug:front:default
audio.device.alsa_front_device:default

# alsa nahasle gailua
# string, default: PCM
#audio.device.alsa_mixer_name:PCM

# soinu txartelak mmap egin dezake
# bool, default: 0
#audio.device.alsa_mmap_enable:0

# 5.1 kanaletako irteerak erabiltzen duen gailua
# string, default: iec958:AES0=0x6,AES1=0x82,AES2=0x0,AES3=0x2
#audio.device.alsa_passthrough_device:iec958:AES0=0x6,AES1=0x82,AES2=0x0,AES3=0x2

# 4 kanaletako irteerak erabiltzen duen gailua
# string, default: plug:surround40:0
#audio.device.alsa_surround40_device:plug:surround40:0

# 5.1 kanaletako irteerak erabiltzen duen gailua
# string, default: plug:surround51:0
#audio.device.alsa_surround51_device:plug:surround51:0

# bozgorailu ordenamendua
# { Mono 1.0  Stereo 2.0  Headphones 2.0  Stereo 2.1  Surround 3.0  Surround 4.0  Surround 4.1  Surround 5.0  Surround 5.1  Surround 6.0  Surround 6.1  Surround 7.1  Pass Through }, default: 1
#audio.output.speaker_arrangement:Stereo 2.0

# offset for digital passthrough
# numeric, default: 0
#audio.synchronization.passthrough_offset:0

# play audio even on slow/fast speeds
# bool, default: 0
#audio.synchronization.slow_fast_audio:0

# audioa eta bideoa sinkronizatzeko metodoa
# { metronom feedback  resample }, default: 0
#audio.synchronization.av_sync_method:metronom feedback

# always resample to this rate (0 to disable)
# numeric, default: 0
#audio.synchronization.force_rate:0

# enable resampling
# { auto  off  on }, default: 0
#audio.synchronization.resample_mode:auto

# abiarazterakoan audio bolumena
# [0..100], default: 50
#audio.volume.mixer_volume:50

# berezarri tamaina maila abiaraztean
# bool, default: 0
#audio.volume.remember_volume:0

# video driver to use
# string, default: auto
#video.driver:auto

# pitch alignment workaround
# bool, default: 0
#video.device.xv_pitch_alignment:0

# autopaint colour key
# bool, default: 0
#video.device.xv_autopaint_colorkey:0

# video overlay colour key
# [0..16777215], default: 66046
#video.device.xv_colorkey:66046

# disable exact alpha blending of overlays
# bool, default: 0
#video.output.disable_exact_alphablend:0

# bideo eskalatze guztiak ezgaitu
# bool, default: 0
#video.output.disable_scaling:0

# irudi horizontal kokalekua irteera lehoan
# [0..100], default: 50
#video.output.horizontal_position:50

# irudi bertikal kokalekua irteera lehoan
# [0..100], default: 50
#video.output.vertical_position:50

# ez-elkarlituriko metodoa (zaharkiturik)
# { none  bob  weave  greedy  onefield  onefield_xv  linearblend }, default: 4
#video.output.xv_deinterlace_method:onefield

# MPEG-4 postprozesatze kalitatea
# [0..6], default: 3
#video.processing.ffmpeg_pp_quality:3

# CD audio-k erabiliko duen gailua
# string, default: /dev/cdrom
media.audio_cd.device:/media/cdrom0

# gutxitu diska gailua abiadura faktore honetara
# numeric, default: 4
#media.audio_cd.drive_slowdown:4

# numeric, default: 1
media.audio_cd.use_cddb:0

# CDDB katxe karpeta
# string, default: /home/jon/.xine/cddbcache
#media.audio_cd.cddb_cachedir:/home/jon/.xine/cddbcache

# CDDB zerbitzari ataka
# numeric, default: 8880
#media.audio_cd.cddb_port:8880

# CDDB zerbitzari izena
# string, default: freedb.freedb.org
#media.audio_cd.cddb_server:freedb.freedb.org

# korronteak gordetzeko karpeta
# string, default: 
#media.capture.save_dir:

# Number of dvb card to use.
# numeric, default: 0
#media.dvb.adapter:0

# Remember last DVB channel watched
# bool, default: 1
#media.dvb.remember_channel:1

# Last DVB channel viewed
# numeric, default: -1
#media.dvb.last_channel:-1

# DVD erreprodukzioaren lehenetsirako hizkuntza
# string, default: en
#media.dvd.language:en

# DVD erreproduktorean eskatzen duen erregioa (1 - 8)
# numeric, default: 1
#media.dvd.region:1

# DVD-a erreproduzitzeko erabiliko den gailua
# string, default: /dev/dvd
media.dvd.device:/media/cdrom0

# DVD irakurleantzat gailu gordin (raw) ezarpenak
# string, default: /dev/rdvd
#media.dvd.raw_device:/dev/rdvd

# irakuketa-goiburu gordetzea
# bool, default: 1
#media.dvd.readahead:1

# CSS desenkriptazio metodoa
# { key  disc  title }, default: 0
#media.dvd.css_decryption_method:key

# play mode when title/chapter is given
# { entire dvd  one chapter }, default: 0
#media.dvd.play_single_chapter:entire dvd

# Bilatuko den untitatea
# { seek in program chain  seek in program }, default: 0
#media.dvd.seek_behaviour:seek in program chain

# Ekintza egingo ez den unitatea
# { skip program  skip part  skip title }, default: 0
#media.dvd.skip_behaviour:skip program

# path to the title key cache
# string, default: /home/jon/.dvdcss/
#media.dvd.css_cache_path:/home/jon/.dvdcss/

# fitxategi kudeatzailearen abiarazte kokalekua
# string, default: /home/jon
#media.files.origin_path:/home/jon

# bistaratu ezkutatuako fitxategiak
# bool, default: 0
#media.files.show_hidden_files:0

# sare zabalera
# { 14.4 Kbps (Modem)  19.2 Kbps (Modem)  28.8 Kbps (Modem)  33.6 Kbps (Modem)  34.4 Kbps (Modem)  57.6 Kbps (Modem)  115.2 Kbps (ISDN)  262.2 Kbps (Cable/DSL)  393.2 Kbps (Cable/DSL)  524.3 Kbps (Cable/DSL)  1.5 Mbps (T1)  10.5 Mbps (LAN) }, default: 10
#media.network.bandwidth:1.5 Mbps (T1)

# Timeout for network stream reading (in seconds)
# numeric, default: 30
#media.network.timeout:30

# Domains for which to ignore the HTTP proxy
# string, default: 
#media.network.http_no_proxy:

# 
# string, default: 
#media.network.http_proxy_host:

# HTTP proxy pasahitza
# string, default: 
#media.network.http_proxy_password:

# HTTP proxy ataka
# numeric, default: 80
#media.network.http_proxy_port:80

# HTTP proxy erabiltzailea
# string, default: 
#media.network.http_proxy_user:

# MMS protokoloa
# { auto  TCP  HTTP }, default: 0
#media.network.mms_protocol:auto

# automatically advance VCD track/entry
# bool, default: 1
#media.vcd.autoadvance:1

# VCD default type to use on autoplay
# { MPEG track  entry  segment  playback-control item }, default: 3
#media.vcd.autoplay:playback-control item

# VCD position slider range
# { auto  track  entry }, default: 0
#media.vcd.length_reporting:auto

# show 'rejected' VCD LIDs
# bool, default: 0
#media.vcd.show_rejected:0

# VCD format string for stream comment field
# string, default: %P - Track %T
#media.vcd.comment_format:%P - Track %T

# VCD debug flag mask
# numeric, default: 0
#media.vcd.debug:0

# CD-ROM drive used for VCD when none given
# string, default: 
media.vcd.device:/media/cdrom0

# VCD format string for display banner
# string, default: %F - %I %N%L%S, disk %c of %C - %v %A
#media.vcd.title_format:%F - %I %N%L%S, disk %c of %C - %v %A

# v4l irrati gailua
# string, default: /dev/v4l/radio0
#media.video4linux.radio_device:/dev/v4l/radio0

# v4l bideo gailua
# string, default: /dev/v4l/video0
#media.video4linux.video_device:/dev/v4l/video0

# WinTV-PVR 250/350 (pvr plugin)-ek erabiliko duen gailua
# string, default: /dev/video0
#media.wintv_pvr.device:/dev/video0

# RealPlayer kodeken bidea
# string, default: /usr/lib/win32
#decoder.external.real_codecs_path:/usr/lib/win32

# path to Win32 codecs
# string, default: /usr/lib/codecs
#decoder.external.win32_codecs_path:/usr/lib/codecs

# azpititulu tamaina
# { tiny  small  normal  large  very large  huge }, default: 1
#subtitles.separate.subtitle_size:small

# azpititulu mugimetu bertikala
# numeric, default: 0
#subtitles.separate.vertical_offset:0

# Azpitituluen letra-tipoa
# string, default: sans
#subtitles.separate.font:sans

# azpitituluen kodifikazioa
# string, default: iso-8859-1
subtitles.separate.src_encoding:utf-8

# erabili eskalagabeko OSD posible bada
# bool, default: 1
#subtitles.separate.use_unscaled_osd:1

# azpititulu bistaratze denbora segundutan
# numeric, default: 4
#subtitles.separate.timeout:4

# sortuko diren segunduko marko kopurua
# numeric, default: 14
effects.goom.fps:15

# goom image height
# numeric, default: 240
#effects.goom.height:240

# goom image width
# numeric, default: 320
effects.goom.width:384

# colour-space conversion method
# { Fast but not photorealistic  Slow but looks better }, default: 0
#effects.goom.csc_method:Fast but not photorealistic

# audio buffer kopurua
# numeric, default: 230
#engine.buffers.audio_num_buffers:230

# numeric, default: 500
#engine.buffers.video_num_buffers:500

# default number of video frames
# numeric, default: 15
#engine.buffers.video_num_frames:15

# a/52 deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.a/52:0

# bitplane deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.bitplane:0

# dts deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.dts:0

# dvaudio deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.dvaudio:0

# dxr3-mpeg2 deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.dxr3-mpeg2:0

# dxr3-spudec deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.dxr3-spudec:0

# faad deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.faad:0

# ffmpeg-wmv8 deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.ffmpeg-wmv8:0

# ffmpeg-wmv9 deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.ffmpeg-wmv9:0

# ffmpegaudio deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.ffmpegaudio:0

# ffmpegvideo deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.ffmpegvideo:0

# flacdec deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.flacdec:0

# gsm610 deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.gsm610:0

# image deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.image:0

# mad deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.mad:0

# mpc deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.mpc:0

# mpeg2 deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.mpeg2:0

# nsf deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.nsf:0

# pcm deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.pcm:0

# qta deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.qta:0

# qtv deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.qtv:0

# real deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.real:0

# realadec deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.realadec:0

# rgb deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.rgb:0

# speex deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.speex:0

# spucc deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.spucc:0

# spucmml deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.spucmml:0

# spudec deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.spudec:0

# spudvb deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.spudvb:0

# sputext deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.sputext:0

# theora deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.theora:0

# vorbis deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.vorbis:0

# win32a deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.win32a:0

# win32v deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.win32v:0

# yuv deskodetzailearen lehentasuna
# numeric, default: 0
#engine.decoder_priorities.yuv:0

# media format detection strategy
# { default  reverse  content  extension }, default: 0
#engine.demux.strategy:default

# xinek erabiltzen duen memoria kopia metodoa
# { probe  libc  kernel  mmx  mmxext  sse }, default: 0
engine.performance.memcpy_method:mmxext

# onartzen den alde batetara utziko marko kopuru ehunekoa
# numeric, default: 10
#engine.performance.warn_discarded_threshold:10

# onartzen den alde batetara utziko marko kopuru ehunekoa
# numeric, default: 10
#engine.performance.warn_skipped_threshold:10

# Onartu aldaketa inplizitoak konfiguraketan (adib. MRL bidez)
# bool, default: 0
#misc.implicit_config:0


---

### Post by Korrontean on 2008-01-16
Thanks virtuoso........yes it does....... :)

---

### Post by Korrontean on 2008-01-16
One more update: outcome of xine-check:
```
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.20-16-lowlatency)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ hint ] multiple xine executables found
         I have found multiple xine executables on your machine:
         /usr/bin/xine
         /usr/X11R6/bin/xine
         xine is the main player as installed by the xine-ui package.
         You should probably uninstall the instances you don't use...
         press <enter> to continue...

[ good ] /usr/bin/xine is in your PATH
[ hint ] No xine-config found. Assuming xine from Debian package
         The xine-config script can be used to determine some file locations
         used by xine-lib, but you don't have such a script on your system.
         However, it looks like you installed xine from the Debian packages.
         So I'll just guess that you are using the standard locations.
         If you want me to be sure about those file locations, you can install
         the 'libxine-dev' package, which contains xine-config. However, this
         package is not really needed to run xine...
         press <enter> to continue...

[ good ] plugin directory /usr/lib/xine/plugins exists.
[ good ] found unknown plugin: *.so
[OUCH!!] There are no input plugins.
         xine needs at least one input plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no demux plugins.
         xine needs at least one demux plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no decoder plugins.
         xine needs at least one decoder plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no video_out plugins.
         xine needs at least one video_out plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[OUCH!!] There are no audio_out plugins.
         xine needs at least one audio_out plugin, but none is installed.
         You should probably reinstall xine-lib...
         press <enter> to continue...

[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/scd0
[ good ] /dev/dvd points to /dev/scd0
[ hint ] Your DVD drive seems not to be attached via ATAPI.
         This might be due to the use of an ide-scsi emulation.
         If you really have a SCSI DVD drive, your SCSI controller is likely
         to do perfect DMA, so there's no reason to worry about this.
         However, if you're using ide-scsi, there is a chance that DMA is
         disabled for the DVD drive. Moreover, I don't know how to enable
         DMA in that case, so you probably have to live with some performance
         loss. (FIXME: check for /proc/ide, provide solution)
         press <enter> to continue...

[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  YUY2 YV12 UYVY I420 RV15 RV16 YVYU NV12 NV21 YUY2 YV12 UYVY I420 YVYU NV12 NV21

```

---

### Post by Nano Geek on 2008-01-16
It sounds like you haven't installed the DVD decryptor plug-in yet.
Did you try the command that I gave you last or the link LaRoza gave you?

---

### Post by Korrontean on 2008-01-16
Hi asjdfwejqrfjcvm msz34rq33!

Welcome back to my awful thread :) and thanks again for your support

If I type this in, as Laroza suggested:

```
sudo mkdir /media/cdrom0
```

I get a message telling me that it's not possible to created the folder because "File exists"

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

This installed something, but no difference.

The link for the documentation, yes, I've gone through every guide I've found, without solution. Getting desperate already ](*,)

Any ideas? THANKS!!!

---

### Post by Nano Geek on 2008-01-17
Sorry for the slow response. 

I'm not exactly sure what to advise you to do.
Have you tried using Totem-xine yet or VLC?

---

### Post by Yellow Pasque on 2008-01-17
Try:
sudo apt-get install ubuntu-restricted-extras
to make sure you have all the packages necessary to clear the legal obstacles.

---

### Post by Korrontean on 2008-01-17
> Have you tried using Totem-xine yet or VLC?

Yes, I have...

> sudo apt-get install ubuntu-restricted-extras

I have done it also...

But some films just don't wanna be played................still get the same error messages.

THANK YOU ANYWAY!

---

### Post by mc4man on 2008-01-18
There are a few things that you could post that would help in either resolving or understanding your issues. Considering it's a laptop the model of dvd drive matters, go to places>computer>right click on the cd/dvdrw icon>properties>drive will show vendor and model.
I don't know much about totem cause that's the first thing i uninstall, better to use vlc. First disable the autoplay option in preferences. Open vlc in the terminal and attempt playback (open disk) of troublesome disk(s) and post the output. If vlc crashes with no errors in console, reopen vlc and use the open directory option (browse to the video_ts in media/cdrom0 ). If vlc again crashes with no console errors then post disk title(s) and region.
For some future info you only need 3 "core" libs for dvd playback - libdvdcss2, libdvdread3, and libdvdnav4. Once those are in place if you install your player of choice (vlc, mplayer,smplayer) you should be good to go. Shouldn't take more than a few minutes. As far as totem additionally installing the gstreamer -plugins-ugly will allow dvd playback. (how good i don't know and wouldn't bother anyway). 
As i said I don't know totem but there is a curious line in the .config you posted. Assuming commented lines are the default then 

```
# DVD erreproduktorean eskatzen duen erregioa (1 -
# numeric, default: 1
#media.dvd.region:1 
```
doesn't make alot of sense assuming your playing region 2 disks on a region 2 drive

edit: I enabled dvd playback of totem and vlc on a laptop that was lying around (had a fresh install of feisty) and totem will have problems with structure protected disks (ARccoSS, ripguard, ect.), while vlc doesn't. There are a handfull of titles that no open source player can play - recent new line cinema (all regions) and few others region 2 only

---

### Post by Korrontean on 2008-01-18
Thanks, mc4man!
> 
Considering it's a laptop the model of dvd drive matters, go to places>computer>right click on the cd/dvdrw icon>properties>drive will show vendor and model.

Vendor: MATSHITA
Model: UJ-840D
Serial:
Firmware: 1.00
Connection: SCSI
Media: CD-RW/DVD+-RW Drive
Removable: Yes (ejectable)
External: No

This is what I get starting VLC from the terminal and then trying to open the DVD:

```

jon@jonatubuntustudiojajaja:~$ vlc
VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: TWIN_PEAKS_COMPLETE_DISC_1
libdvdnav: DVD Serial Number: 3733064f
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/jon/.dvdnav/TWIN_PEAKS_COMPLETE_DISC_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000137
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00012536
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00012536)
libdvdread: Elapsed time 4
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0004e2f7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002fd854
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x002fd854)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002fdb74
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002fdb74)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00301229
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0030636b
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 4
[00000280] main playlist: nothing to play
[00000280] main playlist: stopping playback
```
> 
For some future info you only need 3 "core" libs for dvd playback - libdvdcss2, libdvdread3, and libdvdnav4. Once those are in place if you install your player of choice (vlc, mplayer,smplayer) you should be good to go.

I've installed all of them ;-)

I've just tried a new DVD I was given as a present yesterday :-( and the outcome in VLC is different:

```
jon@jonatubuntustudiojajaja:~$ vlc
VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: UK_101115
libdvdnav: DVD Serial Number: 3B370B84___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/jon/.dvdnav/UK_101115.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000127
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000199
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000199)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000d1de
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000d236
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000d28d
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 3
*** Zero check failed in ifo_read.c:926
    for vts_ptt_srpt->zero_1 = 0xccb7

*** libdvdread: CHECK_VALUE failed in ifo_read.c:928 ***
*** for vts_ptt_srpt->nr_of_srpts < 100 ***

libdvdread: Can't allocate memory for file read!
libdvdread: Unable to read PTT search table.
libdvdnav: ifoRead_VTS_PTT_SRPT failed - CRASHING!!!
vlc: vm.c:202: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)
```

> There are a handfull of titles that no open source player can play - recent new line cinema (all regions) and few others region 2 only

Does this mean there might be no solution?
> 
doesn't make alot of sense assuming your playing region 2 disks on a region 2 drive

I've set the region to 2, using regionset, but there seems to be no change.

One last thing, a fresh install could help? My laptop used to be able to play DVDs without any problem in the past..........

THANK YOU VERY MUCH, MC4MAN................ :-D

---

### Post by Yellow Pasque on 2008-01-18
You're not the only one having issues
[http://ubuntuforums.org/showthread.php?p=4158684](http://ubuntuforums.org/showthread.php?p=4158684)

---

### Post by Korrontean on 2008-01-18
Thanks Temüjin, there seems to be no clear solution though :-(

Well, after restarting my computer, things have changed. Now I can open the DVD menus. When I access the film itself:

With Kaffeine, I get a message that says:

> The source seems encrypted, and can't be read. 
Your DVD is probably crypted. According to your country laws, you can or can't use libdvdcss to be able to read this disc. (Media stream scrambled/encrypted)

With VLC, I will only hear the sound, no video at all, and the sound will be flawed........in the terminal I can read this:
```

jon@jonatubuntustudiojajaja:~$ vlc
VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: TWIN_PEAKS_COMPLETE_DISC_1
libdvdnav: DVD Serial Number: 3733064f
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/jon/.dvdnav/TWIN_PEAKS_COMPLETE_DISC_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000137
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00012536
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0004e2f7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002fd854
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002fdb74
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00301229
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0030636b
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
[00000334] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
[00000354] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
[00000280] main playlist: stopping playback
```

:mad: :mad: :mad:

Well, at least I can see the beautiful DVD menus........and watch the machines in the sawmill in Twin Peaks...

---

### Post by c0met on 2008-01-18
Have you tried running a lens cleaning CD in your drive? It might be that the laser lens just needs to be cleaned up a bit - especially if you use the drive a lot. 

This might have already been suggested. I didn't read through all the replies. Apologies if I am just repeating an idea.

---

### Post by Korrontean on 2008-01-18
Thanks C0met, haven't tried this yet.

---

### Post by perixx on 2008-01-18
> Have you tried running a lens cleaning CD in your drive? It might be that the laser lens just needs to be cleaned up a bit - especially if you use the drive a lot. That might be possible... but it's not very likely if some DVD's play without trouble, I guess.

I'm also having trouble with playing DVD's under Xubuntu here - I'm using MPlayer - some types won't play at all and the player hangs in an endless read/stop loop. 
My drive is a Samsung SH-182D... 
I'm suspecting this drive to not being very compatible to copy protection, for some titles won't play on my PC (even under XP), but will on friend's laptop (XP). 

**Funny, but:** with VLC, which should have all it's codecs and things needed included, I can play some films under XP, which aren't possible under Xubuntu (also VLC) - but not all.

E.g., I can't play back 'Becoming Mayan' on my drive AT ALL. Obviously, this is due to overexaggerated copy-protection-madness (exchanged media at reseller 2 times).... **I returned the media **after those troubles and I advise **everybody else to do likewise** with problematic copy-protected media!

**EDIT:** one option I haven't tried yet, is to set a region code - though I'll probably don't really have any use for changing it again, ever, I'm reluctant to set it fixed... maybe that could be causing issues as well:
> If your DVD player regularly locks up when you try to play back a DVD, your DVD player probably does not match the DVD's [WikiPedia]Region Code. Region Codes are a form of vendor lock-in. For example, you cannot play a DVD published in Japan (Region 2) on a DVD player in the United States (Region 1) without changing the Region Code of the DVD player (unless you own a region free DVD player). You can view or modify the Region Code of your DVD drive with the 'regionset tool' The author of regionset writes: "On delivery, most DVD drives have no region code set. The drive firmware allows you to change the region code, but on nearly all drives you are limited to five (5) changes. After the fifth change, the DVD drive will stay fixed on that code -- on some drives you can upgrade the drive firmware and have then additional five changes, on other drives you won't be able to change the region code any more."

Most players (eg mplayer/vlc) with most DVD drives are able to ignore the value of the region setting. However, it must have been set to something; if it hasn't been initialized, even non-region-restricted DVDs won't play. Also, if it is necessary to crack the CSS key, it can sometimes take up to a few minutes to do so.

**RE-EDIT:** Just have checked region code, it's already set with my drive, so that shouldn't be the culprit.

perixx

---

### Post by Korrontean on 2008-01-18
Thanks for the info, perixx.

Unfortunately I don't have a dual boot, so I cannot watch the movies at all.

I'm thinking of a fresh install to see what happens.

---

### Post by seoexpert on 2008-01-18
It seems that you have been using without any care, but now you can open it and clean lens. I often got it and solved like this. 

[Hank Freid]("http://www.marrakechhotelnyc.com/press.html")
:)

---

### Post by perixx on 2008-01-18
If you want to clean your drive's lens, I advise you to apply some isopropanol (industry-alcohol, get it in a drug-store) on a Q-tip and then, with it's tip, rubbing off the dust/fat/nicotine-film from the lens **VERY CAREFULLY** in tiny circles. 

**DON'T USE HOUSEHOLD/GRAIN ALCOHOL**, it will leave a  milky film on the lens, yet just worsen things!

perixx

---

### Post by mc4man on 2008-01-18
> I'm thinking of a fresh install to see what happens.
Wouldn't be the worst idea - seems you have all sorts of players, codecs ect.  One error does stand out though -```
 libdvdread: Can't allocate memory for file read!
```  If your using kubuntu (you never said) see if libxine1-ffmpeg is installed
Looking at twin peaks (has no structure protection) at first you weren't retrieving the keys, that was resolved by upgrading to libdvdcss 1.2.9 but now  > With VLC, I will only hear the sound, no video at all, and the sound will be flawed which points to a separate video issue.There are many threads on sound, no video - perhaps you can track that issue down.
On UK_101115 (whatever that is) in addition to above error you get (using libdvdcss 1.2.5 )
> Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000199 which is a show stopper right there. Again if using kubuntu the above lib may help.
Generally speaking when you see errors like  ```
Zero check failed in ifo_read.c:926

``` that's indicative of a structure protected title
If you do a fresh install I'd take a simple tunnel vision approach - get your audio, video squared away, install the 3 main libs (latest versions), pick 1 player to install (i say vlc) and see what happens.  I'm partial to ubuntu over kubuntu - honestly it only took a couple of minutes last night from a fresh install to working dvd playback
The quickest, easiest way to get libdvdcss2 (for a fresh install) is just to go to the videolan site and dl/install the deb   [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/)
worst case  - you can purchase and install (in a roundabout way) lindvd which should playback virtually all titles but your inability to play twin peaks points to other issues that would also need to be resolved

Edit : almost forgot - your MATSHITA drive has some unique limitations though it's likely none of your current issues can be attributed to the drive
[http://ubuntuforums.org/showthread.php?t=669795](http://ubuntuforums.org/showthread.php?t=669795)  for a limited explanation

---

### Post by Korrontean on 2008-01-20
Thank you very much, Perixx!
I'll start the fresh install in a few days. We'll see what happens...
Funnily, someone lent an older version of Twin Peaks yesterday and I could watch it without any problem.......
Have a nice day :)

---

