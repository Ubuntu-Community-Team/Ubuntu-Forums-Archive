---
title: "help me out!"
date: 2008-07-22
forum: General Help
---

### Post by justborn on 2008-07-22
i have deleated some important file in my home folderthat is making my sys go mad,but i know sumone can help me out.



all u have to do is"'cd' to the home directory and perrform 'ls-a'"on ur sys & paste the output here 'in colors'(so that i can makeout different types of files).i'll spot out the file from it.(a miximised screenshot of the terminal would make my day)

---

### Post by Het Irv on 2008-07-22
I've got a better idea, do you know what file you deleted?  If not, how is your computer "going mad" maybe we can figure out which one it was.  

The home folder is your personal files, so everyone's is going to be different.

---

### Post by Potatoj316 on 2008-07-22
If there were any files that would make your system "go mad" you would need to be sudo to delete them.  Did you use nautilus to delete them or rm from the command line?  If you used nautilus you could get it from the trash.

I dont think there are any files in the home directory that are needed by the computer to run.  If there are any config files they are probably in hidden (.dirname) directories.

---

### Post by dracayr on 2008-07-22
If you did it via terminal: press Ctrl-R and type rm
If you did it via nautilus, it should be in the trash

dracayr

---

### Post by lamego on 2008-07-22
1) You should use a descriptive title when posting on a forum, "help me" does not help you

2) The default system installed files can be found on /etc/skel

3) You would be better by describing what is your problem, a "mad system" does not help.

Thanks

---

### Post by justborn on 2008-07-23
> **Het Irv said:**
> I've got a better idea, do you know what file you deleted?  If not, how is your computer "going mad" maybe we can figure out which one it was.  

The home folder is your personal files, so everyone's is going to be different.

i dont know the exact file .and i do  know that all comps will have different files.but what i have deleated is a <conf hidden>file.that is why asked out here.

---

### Post by justborn on 2008-07-23
> **Potatoj316 said:**
> If there were any files that would make your system "go mad" you would need to be sudo to delete them.  Did you use nautilus to delete them or rm from the command line?  If you used nautilus you could get it from the trash.

I dont think there are any files in the home directory that are needed by the computer to run.  If there are any config files they are probably in hidden (.dirname) directories.

i did it gui.and it is been a long time .i have emptied the trash ,that is why i am writing this thread


yes it was a hidden file.

---

### Post by Het Irv on 2008-07-23
Can you describe what is wrong with your computer, because even the hidden config files change from computer to computer.

---

### Post by justborn on 2008-07-23
> **dracayr said:**
> If you did it via terminal: press Ctrl-R and type rm
If you did it via nautilus, it should be in the trash

dracayr

why dont u try to help the way the thread starter asks u too


if u would have done it ,in one post i could solved my probo

---

### Post by justborn on 2008-07-23
> **lamego said:**
> 1) You should use a descriptive title when posting on a forum, "help me" does not help you

2) The default system installed files can be found on /etc/skel

3) You would be better by describing what is your problem, a "mad system" does not help.

Thanks

i'll see to that the next time that it is enough discriptive.

i  used it becoz i dint have any specifications and just wanted help from someone,who could without giving suggestions help me in the way i asked.

---

### Post by collinp on 2008-07-23
What specifically is going wrong with your computer?

---

### Post by Joeb454 on 2008-07-23
Please calm down, we're trying to help, so we can help you sort it out.

If you could describe what is happening, we may be able to help further

---

### Post by WRDN on 2008-07-23
> **justborn said:**
> why dont u try to help the way the thread starter asks u too


if u would have done it ,in one post i could solved my probo

For you're benefit, I used the ls-a command in my home folder, and the following appeared:

```
.              .gconf                .qt
..             .gconfd               .quake4
.adobe         .gftp                 .recently-used
.aptitude      .gimp-2.4             .recently-used.xbel
apt.sh         .gksu.lock            .scim
audiofile.wav  .gnome2               .Skype
.azureus       .gnome2_private       .ssh
.Azureus       .gnupg                .subversion
.bash_history  .gpilotd              .sudo_as_admin_successful
.bash_logout   .gpilotd.pid          .swo
.bashrc        .gstreamer-0.10       .swp
.bogofilter    .gtk-bookmarks        .synaptic
.cache         .gvfs                 .themes
cd             .ICEauthority         .thumbnails
               .icons                
.cedega        .isomaster            
.cedegarc      .kde                  .transmission
.clamtk        .lesshst              .tsclient
.codeblocks    .local                .Untitled2
.config        .macromedia           .update-manager-core
.dbus          .mcop                 .update-notifier
Desktop        .mcoprc               .viminfo
.dmrc          .metacity             .VirtualBox
Documents      .mozilla              .vlc
.doom3-demo    .mozilla-thunderbird  .wapi
.dvdcss        .mplayer              .wine
.dvdrip        Music                 .wine-doors
.dvdriprc      .nautilus             .wine.stderr.log
.esd_auth      .netx                 .wine.stdout.log
.evolution     .nvidia-settings-rc   .Xauthority
Examples       .openoffice.org2      .Xauthority-c
.filezilla     Pictures              .Xauthority-l
.fluxbox       .profile              .xchat2
.fontconfig    .pulse                .xscreensaver-getimage.cache
.fr-J9XMRc     .pulse-cookie         .xsession-errors
.gcjwebplugin  .purple               .xvidcaprc

```

As others have already mentioned though, what exactly is the problem?

---

### Post by justborn on 2008-07-23
> **Hellow said:**
> What specifically is going wrong with your computer? Maybe we can recreate the file that you deleted.

please help me in the way i asked help.i know what to do.


becoz u asked ,

i have deleated some 'conf hidden' file (GUI).which has switched on the root (tha is off by default).and the ownership of some applications have changed.which is causing so many errors from booting to the shutting down.i have errors in all logs.

i curently am using the failsafe gnome mode.



//i currently dont have the system in front of me.//
iam unable to use the effects for the post ,becoz i have probo here too.

---

### Post by justborn on 2008-07-23
> **WRDN said:**
> For you're benefit, I used the ls-a command in my home folder, and the following appeared:

```
.              .gconf                .qt
..             .gconfd               .quake4
.adobe         .gftp                 .recently-used
.aptitude      .gimp-2.4             .recently-used.xbel
apt.sh         .gksu.lock            .scim
audiofile.wav  .gnome2               .Skype
.azureus       .gnome2_private       .ssh
.Azureus       .gnupg                .subversion
.bash_history  .gpilotd              .sudo_as_admin_successful
.bash_logout   .gpilotd.pid          .swo
.bashrc        .gstreamer-0.10       .swp
.bogofilter    .gtk-bookmarks        .synaptic
.cache         .gvfs                 .themes
cd             .ICEauthority         .thumbnails
               .icons                
.cedega        .isomaster            
.cedegarc      .kde                  .transmission
.clamtk        .lesshst              .tsclient
.codeblocks    .local                .Untitled2
.config        .macromedia           .update-manager-core
.dbus          .mcop                 .update-notifier
Desktop        .mcoprc               .viminfo
.dmrc          .metacity             .VirtualBox
Documents      .mozilla              .vlc
.doom3-demo    .mozilla-thunderbird  .wapi
.dvdcss        .mplayer              .wine
.dvdrip        Music                 .wine-doors
.dvdriprc      .nautilus             .wine.stderr.log
.esd_auth      .netx                 .wine.stdout.log
.evolution     .nvidia-settings-rc   .Xauthority
Examples       .openoffice.org2      .Xauthority-c
.filezilla     Pictures              .Xauthority-l
.fluxbox       .profile              .xchat2
.fontconfig    .pulse                .xscreensaver-getimage.cache
.fr-J9XMRc     .pulse-cookie         .xsession-errors
.gcjwebplugin  .purple               .xvidcaprc

```

As others have already mentioned though, what exactly is the problem?


can u paste the matter inside the file ".sudo_as_admin_successful"?

---

### Post by collinp on 2008-07-23
can we see the logs?

---

### Post by WRDN on 2008-07-23
For starters, use the following command in the terminal to lock the root account:

```
sudo passwd -l root
```

Create a new user and see if the problem persists when you login with the account.

```
sudo adduser [username]
```

EDIT:

[QUOTE=justborn]can u paste the matter inside the file ".sudo_as_admin_successful"?[/QUOTE]

That refers to a blank file, not a folder.

---

### Post by justborn on 2008-07-23
> **Joeb454 said:**
> Please calm down, we're trying to help, so we can help you sort it out.

If you could describe what is happening, we may be able to help further

i am calm ,and i too wanna get ur help.

---

### Post by justborn on 2008-07-23
> **Hellow said:**
> can we see the logs?

i think i have quoted in a post above that i dont have the sys in front on me.

---

### Post by justborn on 2008-07-23
> **WRDN said:**
> For starters, use the following command in the terminal to lock the root account:

```
sudo passwd -l root
```

Create a new user and see if the problem persists when you login with the account.

```
sudo adduser [username]
```

EDIT:



That refers to a blank file, not a folder.

i think that i have to lock the root 

and already i have an another account ,so tell me how do i reconfigure the ownership of all the applications to this current account(in failsafe gnome  mode) .and please give all the codes in a stretch ,becoz i dont have the sys in font of me.

---

### Post by collinp on 2008-07-23
Hmm, well, relating to your problems with gnome, I would suggest you reinstall it via this command:
```
&#65279;[SIZE=2]sudo aptitude reinstall gnome[/SIZE]
```

---

### Post by Joeb454 on 2008-07-23
> **justborn said:**
> i am calm ,and i too wanna get ur help.

You seemed to be getting a little agitated and aggressive towards other users. It was intended as a polite message :)

May I suggest you post the logs when you're at the system next, so we may assist further :)

---

### Post by justborn on 2008-07-23
> **Joeb454 said:**
> You seemed to be getting a little agitated and aggressive towards other users. It was intended as a polite message :)

May I suggest you post the logs when you're at the system next, so we may assist further :)

kk dude, i am koool

i too whould have added a smile ,but the thing is that i cannot give any effects ,as i have some probo here too.

---

### Post by justborn on 2008-07-23
> **Hellow said:**
> Hmm, well, relating to your problems with gnome, I would suggest you reinstall it via this command:
```
&#65279;[SIZE=2]sudo aptitude reinstall gnome[/SIZE]
```

but i just wanna change the ownership of thing ,and not to reinstall things .is there not any other way.

---

### Post by justborn on 2008-07-23
> **lamego said:**
> 1) You should use a descriptive title when posting on a forum, "help me" does not help you

2) The default system installed files can be found on /etc/skel

3) You would be better by describing what is your problem, a "mad system" does not help.

Thanks

will the the second point thing ,have all the defaults that r to be in the "home" folder.

---

### Post by justborn on 2008-07-28
> **Hellow said:**
> can we see the logs?

here is auth.log

```
Jul 12 21:39:08 appy-desktop bonobo-activation-server (appy-6401): could not associate with desktop session: Failed to connect to socket /tmp/dbus-fKPN4qlq64: Connection refused
Jul 13 14:46:29 appy-desktop dhcdbd: Started up.
Jul 13 14:50:28 appy-desktop dhcdbd: Started up.
Jul 13 14:52:03 appy-desktop bonobo-activation-server (appy-5847): could not associate with desktop session: Failed to connect to socket /tmp/dbus-PgSLSp1rus: Connection refused
Jul 13 14:52:04 appy-desktop pulseaudio[5863]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jul 13 14:52:04 appy-desktop pulseaudio[5863]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jul 13 14:52:04 appy-desktop pulseaudio[5863]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 37286 Hz.
Jul 13 14:52:04 appy-desktop pulseaudio[5863]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Jul 13 14:55:34 appy-desktop aide-cron-daily: terminated because lock /var/run/aide/cron.daily.lock could not be obtaiend.
Jul 13 18:55:19 appy-desktop gnome-power-manager: (appy) Resuming computer
Jul 13 22:09:47 appy-desktop gnome-power-manager: (appy) Resuming computer
Jul 28 19:05:06 appy-desktop gnome-power-manager: (appy) Resuming computer
Jul 28 19:07:34 appy-desktop dhcdbd: Started up.
Jul 28 19:08:09 appy-desktop bonobo-activation-server (appy-6065): could not associate with desktop session: Failed to connect to socket /tmp/dbus-BFYYqW9UiN: Connection refused
Jul 28 19:08:11 appy-desktop pulseaudio[6081]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jul 28 19:08:11 appy-desktop pulseaudio[6081]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jul 28 19:08:11 appy-desktop pulseaudio[6081]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 37286 Hz.
Jul 28 19:08:11 appy-desktop pulseaudio[6081]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Jul 28 19:12:40 appy-desktop aide-cron-daily: terminated because lock /var/run/aide/cron.daily.lock could not be obtaiend.
Jul 28 19:57:35 appy-desktop pulseaudio[6081]: shm.c: shm_open() failed: No such file or directory
Jul 28 19:57:35 appy-desktop pulseaudio[6081]: pstream.c: Failed to import memory block.
```

---

