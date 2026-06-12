---
title: "DVD Movie Playback on NB100?"
date: 2009-06-19
forum: Hardware
---

### Post by natsys on 2009-06-19
Hi ...

I've just got myself a Toshiba NB100 NetBook running Ubuntu 8.04 Remix - it's great!... but, I'd like now to set it up for playing DVDs from an external drive. The Totem Movie Player that comes with the system doesn't work, so can anyone please point me in the direction of instructions on how I can achieve this?

This system being based on the Intel Atom processor, I'm guessing here that I can't just follow the typical instructions for DVD playback in Hardy :confused:

Also ... I've already tried MPlayer but with no success, it just crashes, so I had to de-install it.

Cheers ... Tom.

---

### Post by natsys on 2009-06-20
I've partially solved this issue myself ... partially, because I can now play back movie DVDs under Jaunty 9.04 Remix (which I installed for dual-boot,) but the question remains for DVDs under the Hardy 8.04 Remix.  Not being too experienced at this, I'm assuming that the codecs made available from Jaunty repositories are more 'accommodating to the purpose' than those from Hardy repositories. It all started working in Totem Movie Player (GStreamer version) when I installed 'gnome-codec-install' (plus the other files that came with it) in Jaunty Remix through Synaptic.

So, the bottom line is that I can now play back DVDs when I boot into Jaunty Remix, but not when I boot into Hardy Remix.

I'm interested to know if the Medibuntu folks have any plans to look at making life a bit easier in terms of media related functionality for those of us out there running the Ubuntu Remix versions?

---

### Post by moe19790 on 2009-06-20
well, i have null experience with 8.04 since my first use to ubuntu started with 9.04. But since every thing works fine with 9.04 have u thought about upgrading?!

---

### Post by natsys on 2009-06-20
Yes, it would seem to be the logical thing to do, but I'm being cautious and there's more to the story!

When I got the NB100 I pretty much immediately installed 9.04 in dual boot with 8.04. Initially things looked fine, but because I was experimenting with various system settings, things went haywire with the desktop in 9.04, so I resorted to using the 8.04 recovery disk to reinstate the system back to factory state. This is where I intended to leave it for a while, but since it just would not play DVDs, no matter what I cautiously tried, I got inquisitive again - hence me going back, yet again, to dual boot with 9.04.

Reinstalling the original 8.04 system on the NB100 is no big deal at all, and installing 9.04 isn't a big deal either, apart from the nuisance of all the updates to download! If things go well with the current dual boot set up over a reasonable period, and I don't screw around with it too much, I'll probably go as you suggest for 9.04 full time. The only thing I found when reinstalling both systems, was that 'one' should reboot the system when the installation finishes, even though it doesn't ask you to.

Thanks for the feedback.

---

### Post by sandman652001 on 2009-06-21
you probably need to add the medibuntu repo then install libdvdcss2 to get dvd playback to work

---

### Post by natsys on 2009-06-21
Yes, Medibuntu has been the answer, but I was cautious because of this system being based on the Intel Atom processor. In another forum I was advised to enquire the architecture of the system by using this command **dpkg --print-architecture** This came back as '**i386**' so I proceeded to use the related commands from the Medibuntu site. I didn't know that I could 'enquire' to see what architecture the system was, so again, I've learned something here.

After I installed Medibuntu (Hardy variety) on the 8.04 partition and I'm now able to play back DVDs with no problem. So, I now have the ability to play DVDs in either the 8.04 or 9.04 partitions on this dual boot NB100 system.

Thank you very much for your interest.

---

### Post by PaulReaver on 2009-09-02
After you get the restricted formats installed
little tip!

**copy this to a blank document file **


#!/bin/bash
# mount

gksudo -k /bin/echo "mount iso"

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`

sudo mkdir "/media/$BASENAME"

zenity --info --title "ISO Mounter" --text "$BASENAME e $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"


if sudo mount -o loop -t iso9660 $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS "/media/$BASENAME"
then
if zenity --question --title "ISO Mounter" --text "$BASENAME Successfully Mounted. Open Volume?"

then
nautilus /media/"$BASENAME" --no-desktop
fi

exit 0
else
sudo rmdir "/media/$BASENAME"

zenity --error --title "ISO Mounter" --text "Cannot mount $BASENAME!"

exit 1
fi

[B]
save this file as mountiso.sh[/B]

[B]
copy this to a text file[/B]


#!/bin/bash
# unmount

gksudo -k /bin/echo "unmount iso"

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`

sudo umount "/media/$BASENAME"

sudo rmdir "/media/$BASENAME"

zenity --info --text "Successfully unmounted /media/$BASENAME"

exit 0

[B]
save this as unmountiso.sh[/B]

copy them both to /home/**your user name**/.gnome2/nautilus-scripts


then make them both executable 

in a terminal
sudo chmod +x /home/ **your username**/.gnome2/nautilus-scripts/mountiso.sh

and again in a terminal

sudo chmod +x /home/ **your username**/.gnome2/nautilus-scripts/unmountiso.sh


i use these scripts to mount iso images as if they were dvd drives.
**a bit like daemon tools for xp.**
just right click any iso files you want to use, go down to scripts and select mountiso.sh or unmountiso.sh

usefull for watching movies on a netbook.

---

### Post by PaulReaver on 2009-09-02
to play dvd movies in ubuntu 8.04 you need something called **libdvdread3**
in a terminal type

**sudo apt-get install libdvdread3**


then in a terminal type

**sudo /usr/share/doc/libdvdread3/install-css.sh**


you should now be able to watch dvd's

---

### Post by natsys on 2009-09-02
Thanks for the info Paul ...

This was an OP of mine back in July, and I've fixed the issue since then.  Your advice on how to run .iso files is very useful however, and I'll use that as well.

Much appreciated ... Tom.

---

