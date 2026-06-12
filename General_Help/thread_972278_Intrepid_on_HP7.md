---
title: "Intrepid on HP7"
date: 2008-11-05
forum: General Help
---

### Post by ericmc783 on 2008-11-05
Just wondering the results some of you have had when putting 8.10 on an HP Pavilion DV7 notebook.

In my case, (Model is DV7-1025NR), I was able to install it, and am having just a few probs. The sound does not work correctly (which I am not totally surprized since I had a HELL of a time getting sound to work in XP). I have not taken too much time troubleshooting the issue, but will soon.

2nd problem: Certain applications freeze, when opening a "second window" of the application. for example, Pidgin, I'll have the main window up showing all my contacts. If I double-click on a contact, type a message and press enter, the app instantly freezes, and I have to force quit. This does NOT cause the whole system to freeze, just the particular app does, and I can continue working in other things even while the app is still froze. Pidgin is not the only app where I get this type of behavior.

But save those 2 things, I have had no probs in Intrepid. WiFi works like a charm. Nvidia driver installed eaisily, and I'm able to use desktop effects. 

Can play video, and download, etc.

Just no sound, and certain apps freeze when doing everyday tasks.

Anyone else have any stories for these models?

---

### Post by ericmc783 on 2008-11-11
UPDATE: I actually discovered that the application freezing problem actually was related to the sound issue.

In pidgin, I disabled sounds completely, and I can use it without problems.

Just need to get sound working ok.... something to do with alsa or inter drivers... will research further soon.

---

### Post by ariekanarie on 2008-11-19
ericmc783: I have a DV7-1090. Fixing sound was easy for me:
Add the following line to /etc/modprobe.d/alsa-base
> options snd-hda-intel enable_msi=1

Sound works like a charm for me now, using PulseAudio. Sound works in Amarok, Youtube and Skype. Hope you get it to work.

---

### Post by K3N8 on 2008-12-01
Hi,

I have a HP Pavilion DV7 1120 (AMD Turion/Radeon HD3450) laptop. Although things haven't been easy, everything works fine now. Things that gave me some trouble were:

- Wireless Card (Atheros AR5007)
- Graphics Card + Compiz Fusion (ATI Mobility Radeon HD3450)
- Microphone

The only thing that causes a problem now is th ehibernation and suspend options. They do not work at all.

Gr. Alexander

---

