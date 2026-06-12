---
title: "Unable to update ubuntu 11.10"
date: 2012-01-31
forum: Hardware
---

### Post by fugash2 on 2012-01-31
Good day. I am fairly new to Linux. Trying to teach myself but get frustrated way too often. Decided to join. I am attempting to update ubuntu 11.04; unfortunately I get an error from both the auto update system and when I try the ¨get apt-upgrade and update¨ commands. 

Below is my error message. Hoping someone will be able to assist in pointing me in the right direction. Thanks in advance:

```
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F
W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Paddy Landau on 2012-02-01
Are you trying to **update** or **upgrade** 11.04?

If it's an update, you have a questionable entry in your list of repositories:
```
W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  oneiric Release: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY A6DCF7707EBC211F
```That line reads "oneiric". It should not do so.

Let us know whether you are updating or upgrading, and we'll go from there. Also tell us whether this is WUBI or a normal installation.

---

### Post by fugash2 on 2012-02-01
Hello Paddy,

I´m excited I´ve received a response. THANK YOU. 

I am attempting to update. My update manager keeps popping up. When I click install updates, it stops and gives me an error message:

¨The action would require the installation of packages from not authenticated sources.¨

when I expand details, it reads:

brasero brasero-cdrkit brasero-common compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default gnome-shell gnome-shell-common libbrasero-media3-1 libdecoration0 liblightdm-gobject-1-0 lightdm linux-firmware linux-headers-3.0.0-16 linux-headers-3.0.0-16-generic linux-image-3.0.0-16-generic linux-libc-dev vino

I obviously have no idea what the above means. 

I then attempted to use the terminal. That´s where I am now. Hopefully what I provided gives you an idea of where I´m stuck.

Thanks again in advance for any assistance.

---

### Post by Paddy Landau on 2012-02-01
> **fugash2 said:**
> I´m excited I´ve received a response. THANK YOU.
Well, I saw no one else had answered. I'm no expert in this but I did spot that inconsistency: oneiric when trying to update natty.

Please open your *Software Sources* application. Press on the *Other Software* tab. Expand the window (if necessary) so that you can see everything listed. Take a screen-shot and attach it please, so I can see what you have.

(There should be a way to do this via a terminal, but I don't know how.)

---

### Post by upchucky on 2012-02-01
the reference to Oneric is in error because the software sources has been changed somehow. You should have only got this error by attempting to Upgrade not Update.
you can select the software sources servers in the update manager, mine are set to main server and or united states.

the other two errors look like they are trying to get the updates from your cdrom drive.

there are settings in the update manager that you can change to de-select the cdrom as a package source.

---

### Post by fugash2 on 2012-02-01
> **Paddy Landau said:**
> Well, I saw no one else had answered. I'm no expert in this but I did spot that inconsistency: oneiric when trying to update natty.

Please open your *Software Sources* application. Press on the *Other Software* tab. Expand the window (if necessary) so that you can see everything listed. Take a screen-shot and attach it please, so I can see what you have.

(There should be a way to do this via a terminal, but I don't know how.)
Thanks again for your reply paddy. Below is my screen shot. Hope this works:

[IMG]http://i303.photobucket.com/albums/nn155/awoc3/39825913.png[/IMG]

---

### Post by fugash2 on 2012-02-01
Hello Chuck,

thanks for your help. 

I´ve unchecked CDROM as source and retried install. Still getting my error message.

---

### Post by Paddy Landau on 2012-02-02
Your software sources have most definitely been modified.

[LIST]
[*]You have *Canonical Partners* twice (ignore the entries that say *Source Code*). It should be only once.
[*]You have Cdrom twice.
[*]Why do you have ubuntu-mozilla-security? That's the one giving you your problem; it is set for oneiric. There is no need to have it, as Ubuntu sends regular updates to Firefox.
[/LIST]
This is what you can do:

[LIST=1]
[*]Untick both Cdrom entries if you haven't already done so.
[*]Untick all the entries that say *Source Code*, as you don't need them (unless you are a programmer wanting to change the programs).
[*]If you click on *Canonical Partners* and press Edit, the URI should read "http://archive.canonical.com/ubuntu", the distribution "natty", and the Components "partner". Keep one of them ticked, and untick the other.
[*]The equivalent settings for *Independent* should read "http://extras.ubuntu.com/ubuntu", "natty" and "main" respectively.
[*]I don't know what *Unsupported Updates* should read, but are you sure you want it?
[*]If you really want ubuntu-mozilla-security (the last two entries), edit them and change *oneiric* to *natty*. However, it may be better to just untick them.
[/LIST]
Close Software Sources; return to Update Manager; press *Check*; *Install Updates* if necessary. Let us know what happens.

---

### Post by fugash2 on 2012-02-02
> **Paddy Landau said:**
> Your software sources have most definitely been modified.

[LIST]
[*]You have *Canonical Partners* twice (ignore the entries that say *Source Code*). It should be only once.
[*]You have Cdrom twice.
[*]Why do you have ubuntu-mozilla-security? That's the one giving you your problem; it is set for oneiric. There is no need to have it, as Ubuntu sends regular updates to Firefox.
[/LIST]
This is what you can do:

[LIST=1]
[*]Untick both Cdrom entries if you haven't already done so.
[*]Untick all the entries that say *Source Code*, as you don't need them (unless you are a programmer wanting to change the programs).
[*]If you click on *Canonical Partners* and press Edit, the URI should read "http://archive.canonical.com/ubuntu", the distribution "natty", and the Components "partner". Keep one of them ticked, and untick the other.
[*]The equivalent settings for *Independent* should read "http://extras.ubuntu.com/ubuntu", "natty" and "main" respectively.
[*]I don't know what *Unsupported Updates* should read, but are you sure you want it?
[*]If you really want ubuntu-mozilla-security (the last two entries), edit them and change *oneiric* to *natty*. However, it may be better to just untick them.
[/LIST]
Close Software Sources; return to Update Manager; press *Check*; *Install Updates* if necessary. Let us know what happens.
Paddy,

THANK YOU SO MUCH. I did exactly as you advised and now I´M GOOD! Sincerely appreciated!!!!!

Upchucky, 

thank you as well for your assistance. 

So far, loving the fact that I switched from windows. I´m learning, with folks like you, makes it a lot easier.  

Thanks again.

---

### Post by Paddy Landau on 2012-02-02
I'm glad it's resolved. It's a bit of a mystery how you came to have those strange entries, though!

If everything is OK, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by fugash2 on 2012-02-02
Not sure either. Had to have been something I did wrong. Going forward, I will check in here prior to doing my own thing. I´m truly WET BEHIND the ears when it comes to Linux. Will mark thread resolved.

THX P...

---

