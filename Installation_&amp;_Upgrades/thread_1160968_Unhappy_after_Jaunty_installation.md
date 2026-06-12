---
title: "Unhappy after Jaunty installation"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by shinmai on 2009-05-16
I hadn't used Ubuntu in a while, (I run Debian on my desktop and use my laptop to try out other distros out of interest, the last Ubuntu release I'd installed was Feisty) and when Jaunty came out I thought I'd give it a go again.

I got a disc from a friend, and popped it in, and did a quick install alongside Vista on my HP Pavilion dv5-1021. The first boot went flawlessly, and I was very pleasantly surprised with all of it - 20 seconds (-ish) from poweron to desktop, wifi worked 'out of the box', as did X (with Feisty, I had to manually edit xorg.conf to use the right driver) and most impressive of all, suspend to disk, which hasn't worked without manual tweaking on any other distro with my dv5. I'd had my opinion of Ubuntu altered hugely, and powered down for the night and thought I'd do some more testing in the morning.

When I booted the OS up I was annoyed to find that the WLAN wouldn't connect to my AP, but merely asked for the passcode, but never established a connection. I tried to connect to one of my other APs with no success, and - on a whim - tried to disable and re-enable wireless networking in gnome network applet. What this acieved, was that now the network applet couldn't even get a list of APs, let alone connect to one.
At this point I was already running late for work, and just wanted to check my mail before leaving, so I rebooted to Vista, only to find to my horror, that I still couldn't find any wireless networks, or manually connect to my APs. I have no idea what the heck ubuntu installer or gnome network applet did, but it has now effectively managed to disable my onboard wireless adapter, and I have no idea how to re-enable it in either OS, the wifi switch on the laptop doesn't do anything, either.

All in all, I can't say that I'm too happy with how my Jaunty installation worked out, and hope HP, or someone here can shed some light on why disabling an option in a windowmanagers network helper seems completely disable the network hardware, and how one would revert such a change.

---

### Post by coffeecat on 2009-05-16
Two suggestions:

I read on another forum that with some wireless chipsets (do you know which yours is, by the way?), the firmware needs to be loaded into the chip from a cold boot. If you do a warm reboot from one OS to another, it stops working. But if you do a cold boot you should be fine. I have no idea whether this is true, but I pass it along in case it has some merit.

Second - I had something similar happen on my very new Sony Vaio on which I had set up a Vista/Jaunty dual-boot. After working fine for a few days, neither Vista nor Jaunty would activate the wireless. The little switch on the front was on, but the light didn't come on. After a few heart-stopping moments I discovered that it was Vista - or more accurately Sony - that was the culprit. On the Vista desktop there's a special Vaio applet to enable one to switch easily (with a mouse/touchpad click) from wireless to ethernet to dial-up modem. Too damn easy! :evil: I must have tapped on it by mistake. Tapping on the wireless checkbox (which glows! :( ) switched on the wireless again and since then all has been well. Except for that ridiculous applet on my Vista desktop. I'd like to uninstall it, but I daren't.

I don't know whether HP has a similar applet, but it might be worth checking to see.

Hope you get this fixed.

---

### Post by shinmai on 2009-05-16
> **coffeecat said:**
> some wireless chipsets (do you know which yours is, by the way?)
I'm at work so I can't check the exact chipset model, but it's a broadcom-adapter.

> **coffeecat said:**
> But if you do a cold boot you should be fine.I shut down the computer to reboot, so sadly no help there..

> **coffeecat said:**
> I don't know whether HP has a similar applet, but it might be worth checking to see. It does, but it doesn't shut down the wireless hardware, but just disables the wireless connection, as if the user had selected Disable in Manage Network Connections. Plus between the wireless working and not working, I didn't even boot to Vista (1. wireless works, I shut down from Vista, 2. reboot to Jaunty-installer, finish the installer and reboot, wireless still works, 3. shut down Jaunty, 4. boot up Jaunty in the morning and wireless doesn't work, 5. cold boot to vista and find out wireless doesn't work, 6. panic)

Thans for your reply, but sadly, I've already tried coldbooting and fiddling with enable/disable wireless-settings both vista and gnome.

---

### Post by pauna on 2009-05-16
Have you checked in BIOS that the wireless device is activated? I have experienced a couple of times situations where for some unknown reasons (sunspots?) the device had magically been disabled in BIOS. Highly annoying.

---

### Post by ugm6hr on 2009-05-16
Not really sure what happened here, but perhaps we might be able to solve the problem if you give a little more detail.

Plug the laptop into the ethernet (wired) connection, and get the latest updates.

```
sudo apt-get update
sudo apt-get upgrade
```

Then give us the complete output from the following commands so that we know what we're dealing with:

```
lshw -class network
ifconfig
iwconfig
```

Also, what encryption do you use?  What channel do you use on the AP?

---

