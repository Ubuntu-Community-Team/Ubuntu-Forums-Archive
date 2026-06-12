---
title: "Sound half operational on Sony Vaio - possible OSS/ALSA conflict"
date: 2010-09-25
forum: Hardware
---

### Post by .broken. on 2010-09-25
Hello everyone,

Just installed Ubuntu for the first time today... It's taken me 2 years to get round to doing it, lol :)

Here's the problem:

Sony Vaio laptop (VGN-FW11E) which up until this morning had Vista installed. After the installation process was complete, there was sound. I then went on to install Wine and Spotify, set Wine up to work with OSS as suggested on the Spotify website and all was going well. Until I loaded a flash video and realised that only Spotify was able to produce sound. Skype, firefox, ubuntu, etc. didn't work. I've been googling ever since. I have Pulse Audio volume control installed, as well as some ALSA modules as per various suggestions with other people's problems. Can't recall all the changes I've made ... :S

After a few hours away from the computer - which incidentally crashed upon stirring it from its sleep mode forcing me to hard reboot - now everything works apart from Wine/Spotify.

As a result, I've come to a conclusion that OSS and ALSA don't get along. Does anyone have any suggestions on how to get everything working?

---

### Post by lkjoel on 2010-09-25
> **.broken. said:**
> Hello everyone,

Just installed Ubuntu for the first time today... It's taken me 2 years to get round to doing it, lol :)

Here's the problem:

Sony Vaio laptop (VGN-FW11E) which up until this morning had Vista installed. After the installation process was complete, there was sound. I then went on to install Wine and Spotify, set Wine up to work with OSS as suggested on the Spotify website and all was going well. Until I loaded a flash video and realised that only Spotify was able to produce sound. Skype, firefox, ubuntu, etc. didn't work. I've been googling ever since. I have Pulse Audio volume control installed, as well as some ALSA modules as per various suggestions with other people's problems. Can't recall all the changes I've made ... :S

After a few hours away from the computer - which incidentally crashed upon stirring it from its sleep mode forcing me to hard reboot - now everything works apart from Wine/Spotify.

As a result, I've come to a conclusion that OSS and ALSA don't get along. Does anyone have any suggestions on how to get everything working?
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by .broken. on 2010-09-26
Afraid that didn't improve the situation, although the sound quality in flash has improved!

Wine and Spotify still don't play sound and Skype doesn't either... The system sounds in Gnome don't seem to work also. I think there's a work around for all of these but I have encountered the following problems:

** 1. Attempting to get Gnome to use OSS**

As per the first link you gave, I added these PPAs ([https://launchpad.net/~dtl131/+archive/ppa]("https://launchpad.net/%7Edtl131/+archive/ppa")). All installed except the last one, libcanberra.

```
$ sudo apt-get install libcanberra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libcanberra

```This might explain why Gnome doesn't play sound...

** 2. Wine**

In an attempt to fix Wine & Spotify, I attempted to install libwine-oss as per [http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4#wine](http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4#wine).

To which I got a similar response as the above...

```
$ sudo apt-get install libwine-oss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libwine-oss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libwine-oss has no installation candidate

```

**3. Skype**

[http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4#2.1_beta:](http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4#2.1_beta:)
I decided to try installing Pulseaudio as recommended. That went off without a hitch. But to get Pulseaudio to use OSS I need to edit /etc/pulse/default.pa. A gedit command should do it, but the file is read only. I tried logging in as root but Ubuntu doesn't let me.

Any help would be appreciated.

Many thanks,
James

---

### Post by lkjoel on 2010-09-26
> **.broken. said:**
> Afraid that didn't improve the situation, although the sound quality in flash has improved!

Wine and Spotify still don't play sound and Skype doesn't either... The system sounds in Gnome don't seem to work also. I think there's a work around for all of these but I have encountered the following problems:

** 1. Attempting to get Gnome to use OSS**

As per the first link you gave, I added these PPAs ([https://launchpad.net/~dtl131/+archive/ppa]("https://launchpad.net/%7Edtl131/+archive/ppa")). All installed except the last one, libcanberra.

```
$ sudo apt-get install libcanberra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libcanberra

```This might explain why Gnome doesn't play sound...

** 2. Wine**

In an attempt to fix Wine & Spotify, I attempted to install libwine-oss as per [http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4#wine](http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4#wine).

To which I got a similar response as the above...

```
$ sudo apt-get install libwine-oss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libwine-oss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libwine-oss has no installation candidate

```

**3. Skype**

[http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4#2.1_beta:](http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4#2.1_beta:)
I decided to try installing Pulseaudio as recommended. That went off without a hitch. But to get Pulseaudio to use OSS I need to edit /etc/pulse/default.pa. A gedit command should do it, but the file is read only. I tried logging in as root but Ubuntu doesn't let me.

Any help would be appreciated.

Many thanks,
James
In Post-Fix your sound!, download the script into your homedir.
Then type this into a Terminal window:
```
cd ~
chmod +x CPanel.sh
./CPanel.sh osspart1
# RESTART COMPUTER NOW
./CPanel.sh osspart2
./CPanel.sh -r

```

---

### Post by .broken. on 2010-09-26
Seems to have worked, despite the -r telling me "OSS not installed properly. Please run ./CPanel.sh -1, reboot, and run ./CPanel.sh -2"

Thank you so much! Now just to get my microphone working, lol :)

---

