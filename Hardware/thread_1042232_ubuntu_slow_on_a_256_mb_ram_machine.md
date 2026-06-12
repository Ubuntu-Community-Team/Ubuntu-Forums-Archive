---
title: "ubuntu slow on a 256 mb ram machine"
date: 2009-01-17
forum: Hardware
---

### Post by ciuci on 2009-01-17
i installed ubuntu on a friend's computer and she has only 256mb of ram. it's sometimes really slow! do you have any idea how to make it quicker? using xfce instead of gnome solves the problem partially but she'd prefer gnome, and xfce is also not fast enough. this is a computer that ran windows xp faster :( ... (as i said it has only 256 mb of ram and a AMD Athlon XP 1800+ processor)


later edit: the display also flickers from time to time, it's really annoying!

---

### Post by lykwydchykyn on 2009-01-17
I've seen a lot of speed tweaks, you can usually find them pretty easily if you search for something like "ubuntu speed tweaks"; honestly though I don't think most of them make much difference.  The single biggest things you can do are (1) disable services you aren't using, and (2) use lighter software.  

I am afraid I don't use GNOME or I might be able to tell you some background services you can disable, but I would certainly switch off desktop effects unless the video card is really awesome (which I wouldn't expect on a machine with 256 MB).

can you post the output from this command (it will show us what services start at boot): 
```

ls /etc/rc2.d/S*

```
There might be some you can safely switch off.

256MB is not much for using GNOME, though.

---

### Post by nick09 on 2009-01-17
You are on borderline with the specs of her computer. What is the model number of the computer? You can find this on the front of the sace most of the time.

---

### Post by ciuci on 2009-01-17
to lykwydchykyn:

these are the services:

/etc/rc2.d/S01policykit                 /etc/rc2.d/S21aumix
/etc/rc2.d/S05vbesave                   /etc/rc2.d/S24hal
/etc/rc2.d/S10acpid                     /etc/rc2.d/S25bluetooth
/etc/rc2.d/S10powernowd.early           /etc/rc2.d/S25pulseaudio
/etc/rc2.d/S10sysklogd                  /etc/rc2.d/S28NetworkManager
/etc/rc2.d/S10xserver-xorg-input-wacom  /etc/rc2.d/S30gdm
/etc/rc2.d/S11klogd                     /etc/rc2.d/S30system-tools-backends
/etc/rc2.d/S12dbus                      /etc/rc2.d/S89anacron
/etc/rc2.d/S14avahi-daemon              /etc/rc2.d/S89atd
/etc/rc2.d/S20apmd                      /etc/rc2.d/S89cron
/etc/rc2.d/S20apport                    /etc/rc2.d/S90binfmt-support
/etc/rc2.d/S20cups                      /etc/rc2.d/S98usplash
/etc/rc2.d/S20fancontrol                /etc/rc2.d/S99acpi-support
/etc/rc2.d/S20hddtemp                   /etc/rc2.d/S99laptop-mode
/etc/rc2.d/S20hotkey-setup              /etc/rc2.d/S99rc.local
/etc/rc2.d/S20powernowd                 /etc/rc2.d/S99rmnologin
/etc/rc2.d/S20rsync                     /etc/rc2.d/S99stop-readahead

do you know any other REALLY userfriendly window manager/desktop enviroment that is less ressource-hungry? ... (in my book xfce does not qualify)

to nick09:
what is a sace? ... if you meant case, i don't think there is such thing as a model number, i must mention this computer is actually formed out of parts not needed on different other computers

---

### Post by nick09 on 2009-01-17
Yes I did mean case. I was just typing too fast to notice.

Well... Then you need to find out what motherboard you have. Run this command in the terminal:
```
sudo lshw -html > (insert-file-name-here).html
```

Then Click Places --> Home and find the file. Then all you need to do is research the motherboard for what memory it supports and graphics cards(saves some RAM) it can handle. You can copy it over to Documents for future reference when she will need it.

EDIT: I read over your first post again and you say the monitor flickers? Is it a CRT Monitor? She can get a LCD monitor then and it will also save her money in the energy bill also.

---

### Post by lykwydchykyn on 2009-01-17
Honestly, if xfce is not friendly enough, I doubt any lighter options will be; other than LXDE, the other options are mostly stripped down window managers and you have to piece together various other tools (file browser, desktop icons, etc).  Friendliness usually costs computing power.

You can disable service by changing the name of the symlink from S(whatever) to K(whatever) (K is for kill, S for start).  Or use the update-rc.d command, but I never could get the hang of its syntax.

The services you could probably do without:
- rsync
- apport (it's a bug reporting service)
- bluetooth (if you have no bluetooth devices)
- klogd (kernel logging, though you lose some debugging info in the event of a crash)
- xserver-xorg-wacom (if you don't have a wacom graphics tablet)

Since it's not a laptop, and if you don't want to use suspend/hibernate features, you can lose:
- vbesave
- laptop-mode

There're probably a few more, but those are the ones I feel safe advising.  If anyone knows any reason why these services should not be disabled, let him speak now or forever hold his peace.

I can't say that that will make a significant difference, 256 is just not much ram for a modern desktop like GNOME.  I don't know what RAM costs in Romania, but over here in the States another 256 MB of old RAM like that (I'm guessing 168 pin SDRAM, maybe DDR1?) can be found second hand for less than the price of lunch.

---

