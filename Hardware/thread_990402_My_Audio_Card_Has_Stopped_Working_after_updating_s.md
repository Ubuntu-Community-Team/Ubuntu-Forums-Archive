---
title: "My Audio Card Has Stopped Working after updating software"
date: 2008-11-22
forum: Hardware
---

### Post by Valinski on 2008-11-22
Hello All,
          I have just bought a toshiba nb100 netbook. I powered it up and updated the system when prompted. After the restart I noticed the sound was muted. Upon pressing the speaker icon I received the following message;

"[COLOR="Red"]No volume control Gstreamer plugin and/or devices found[/COLOR]"

Also when I try to play a sound file I get the following error;
[COLOR="Red"]
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect stream: Invalid argumen[/COLOR]

Any help would be really appreciated.

---

### Post by Valinski on 2008-11-22
Managed to find a solution on the toshiba website;

The solution that worked for me was to;

1- Open Terminal
2- Type [COLOR="Red"]sudo mv /lib/modules/2.6.24-19-lpia/updates/sound ~/sound[/COLOR]
3- Enter your password
3- Type [COLOR="Red"]sudo depmod -a[/COLOR]
4- Restart machine

Then the sound worked again for me

---

