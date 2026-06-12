---
title: "Help pairing MS Surface Ergonomic Keyboard"
date: 2020-09-11
forum: Hardware
---

### Post by FrancoNero on 2020-09-11
Hi everyone. After googling my heart out, I still can't seem to get the pretty neat Microsoft Surface Ergonomic Keyboard to pair.
I run a 2nd generation Dell XPS 13 with Ubuntu 20.04.1 with all updates applied.
Bluetooth is on and works (I can pair some other things). The keyboard works, I could pair it with an Android tablet I have close by (unable to pair it with two different android phones, though).
The keyboard shows up both in the UI (bluetooth settings) as well as in bluetoothctl (but only the mac adress, not the name... I figured out which one it was by attempting to pair from the UI and then seeing in the terminal which one tried and failed).
The key issues is: I am not prompted to enter a PIN to pair, so the pairing fails. Now I am wondering: what can be done? Is the bluetooth driver equipped with all it needs to connect to this thing? I have a tendency to say: I don't accept the fact that this stuff doesn't just work out of the box, this isn't Ubuntu 14.04 anymore... :)
Any help is greatly appreciated!

---

### Post by Tadaen_Sylvermane on 2020-09-11
I don't know for sure. I do know that I had to install a pulseaudio blutooth module even though bluetooth was installed for my headset. It could see it but not connect.

Maybe some kind of similar situation? I googled for bluetooth input devices. Make sure the package bluez-tools is installed. I'm thinking it may already be, but I've been wrong about bluetooth before.

---

### Post by FrancoNero on 2020-09-14
I believe Bluez is not installed on 20.04 and Bluetooth works fine, without it - just not with this keyboard. Not sure now why Bluez is l isted as "the" Ubuntu BT stack but not installed, wondering what it is that is running BT by default on Ubuntu.
I am a bit hesitant about installing any number of (possibly cross-interfering) bluetooth management tools... partially because I am of the "this stuff should work out of the box" conviction :))

Edit: this explains what is what [https://core.docs.ubuntu.com/en/stacks/bluetooth/bluez/docs/bluetooth-on-ubuntu-core](https://core.docs.ubuntu.com/en/stacks/bluetooth/bluez/docs/bluetooth-on-ubuntu-core)

---

### Post by FrancoNero on 2020-09-14
Lo and behold: I installed the Bluez snap, which also prompted a core snap update. And now, even though the BT scan shows the keyboard three times, the last of the three entries finally prompts a pin, and the pairing works!

---

