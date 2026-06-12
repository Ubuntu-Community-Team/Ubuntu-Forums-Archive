---
title: "My bluetooth hreadset Logitech H600 is totally silent"
date: 2022-01-17
forum: Hardware
---

### Post by hnpilot on 2022-01-17
I am a longtime Linux user (10y+), but only on the server side. Now I bought a new computer and decided to use Linux also on the desktop.

I have installed Ubuntu 21.10 and everything else works fine, except that I don't get any sound from my H600 headset. The computer is dual-boot with Windows and there the headset works without any problems.

MB is Asus TUF Gaming B550-PLUS.

Sound works perfectly with my wired H340 (taken from my employers computer for test)

On the settings sound page H600 is visible in sound device selection drop-down when on, has sound level up but no sound happens when I click the sound producing buttons.

I am not 100% sure but I think that the headphones were working after the installation. I had some problems with my NVidia graphics (dual-display) though and followed some instructions to drop the drivers and re-install them.

If it has any significance my Bluetooth mouse works also well on Ubuntu.

Any ideas how to solve the problem?

hannu

---

### Post by him610 on 2022-01-18
How is the h600 headset energized?
In *blueman-manager*, is your h600 headset listed on the Device page?
Has the h600 been setup, paired, trusted, connected?

---

### Post by mIk3_08 on 2022-01-18
> **hnpilot said:**
> I am a longtime Linux user (10y+), but only on  the server side. Now I bought a new computer and decided to use Linux  also on the desktop.
I have installed Ubuntu 21.10 and everything else works fine, except  that I don't get any sound from my H600 headset. The computer is  dual-boot with Windows and there the headset works without any problems.
MB is Asus TUF Gaming B550-PLUS.
Sound works perfectly with my wired H340 (taken from my employers computer for test)
On the settings sound page H600 is visible in sound device selection  drop-down when on, has sound level up but no sound happens when I click  the sound producing buttons.
I am not 100% sure but I think that the headphones were working after  the installation. I had some problems with my NVidia graphics  (dual-display) though and followed some instructions to drop the drivers  and re-install them.
If it has any significance my Bluetooth mouse works also well on Ubuntu.

Any ideas how to solve the problem?

hannu


I think any devices can be paired/connected via bluetooth in you Linux Ubuntu Operating System Machine. I successfully paired my Headset  to my laptop machine with Linux Ubuntu Operating System without any use of BluetoothManager. I think BluetoothManager is intended only for transferring data from your Linux Ubuntu System machine to the device connected via Bluetooth. Here are some command line that you can use in your terminal when you are try to pair your headset using cli (Command Line Interface). This method is more faster and accurate than gui. Here are the command below;

```
bluetoothctl
power on
scan on
discoverable on
pair 
trust
```

---

### Post by him610 on 2022-01-18
@mlk3_08 Thanks for the CLI steps. Learn something new every day.

---

### Post by mIk3_08 on 2022-01-18
> **him610 said:**
> @mlk3_08 Thanks for the CLI steps. Learn something new every day.
You are very much welcome him610;14076261. Good Luck and Cheers to the Linux World.

---

### Post by hnpilot on 2022-01-31
Hello and sorry for the delay on answering, been extremely busy at my work

I finally got the H600 working but I am still quite perplexed about it.

The solution was moving the dongle from a USB-port on my display to the port directly on the computer. Never suspected that as it works fine on Windows also from the display. 

Another strange thing is that none of bluetooth apps referred on your  answers (bluetooth-manager, bluetoothctl) didn't work at all and the Bluetooth service is dead and keeps being dead even after the service  restart. 

lsusb was what I used to see the adapters and before there was Logitech unifying receiver, but not H600. I took the dongle away and re-inserted it with no luck. But when I pushed it in the computer USB socket it showed up in lsusb and after that the headphones started to work. Maybe I don't think too much of the BT mystery any more, if it works, it works... 

Thank you all for the help.

hannu

---

