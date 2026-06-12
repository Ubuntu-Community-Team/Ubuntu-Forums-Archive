---
title: "Problem with nvidia drivers"
date: 2023-10-11
forum: Hardware
---

### Post by Dedalo on 2023-10-11
Hi there.  I have bought this new laptop Asus rog strick ryzen 9 7945hx nvidia 4060. I have a dual boot. When I try to shut down the system, this message appears (see the attached file). Before installing the nvidia proprietary drivers this issue didn't occur, but I had other problems.

Any idea on how to fix this?

---

### Post by Autodave on 2023-10-11
Couple thoughts: what driver are you using?  If the 535 try reverting to the 525 driver.  Also, with that newer equipment, you need the newer kernel: 6.1 I believe.  Hopefully someone will jump in here and tell you how to get that kernel......I can't get to my notes for some reason.....ugh.

---

### Post by Autodave on 2023-10-12
The 6.2 kernel should be available via the Update Manager.

---

### Post by Dedalo on 2023-10-12
> **Autodave said:**
> The 6.2 kernel should be available via the Update Manager.

Hi. Thank you for your feedback. 

The thing just got worse. When I started the system today, apparently the wireless internet connection wasn't working. Tried to open the internet navigator, and nothing happened. Opened a terminal, did sudo apt update, and nothing happened. 

Then I tried to restart the system, and the error of the image appeared. But it got stuck there, until now after a few minutes it would restart or shut down. This time I had to force it using the power button. Now I restarted the system, connected with the ethernet cable. When I do sudo apt update, it asks me for my password, and then it gets stuck in there.

It looks like I have already installed the 6.2 kernel version

:~$ uname -r
6.2.0-34-generic

When I try to open the "additional drivers" thing, it doesn't work either.

---

### Post by Dedalo on 2023-10-12
Now the terminal isn't opening either.

---

### Post by Dedalo on 2023-10-12
Ok. It looks like its fixed now. I entered into the recovery mode. Opened a terminal in there with ctrl+alt+f2, and did the sudo apt update and upgrade. It think that did something with the drivers, because I saw something related to nvidia. Then restarted, and tried to shutdown and restart a couple of times, and none of the issues is seeming to occur anymore. But just a second ago a message appeared saying that an internal error occurred in ubuntu. 

Given that it seems to be working ok, I will avoid going to the 525 version of the driver, unless issues appear again.

BTW, some warning messages appear when doing the sudo apt update:

[I]$ sudo apt update
[sudo] password for enzo: 
Get:1 [https://apt.repos.intel.com/oneapi](https://apt.repos.intel.com/oneapi) all InRelease [4,451 B]
Hit:2 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease                  
Err:1 [https://apt.repos.intel.com/oneapi](https://apt.repos.intel.com/oneapi) all InRelease                     
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BAC6F0C353D04109
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Hit:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Fetched 4,451 B in 2s (2,607 B/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
9 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://apt.repos.intel.com/oneapi](https://apt.repos.intel.com/oneapi) all InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BAC6F0C353D04109
W: Failed to fetch [https://apt.repos.intel.com/oneapi/dists/all/InRelease](https://apt.repos.intel.com/oneapi/dists/all/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BAC6F0C353D04109
W: Some index files failed to download. They have been ignored, or old ones used instead.

[/I]The intel compiler kind of updates everytime I try with sudo apt upgrade. But this issue also happens in another computer I use to work, so I don't think it to be related with the nvidia problem.

---

### Post by Dedalo on 2023-10-13
The issue appeared again yesterday when turning my computer off. I might try to change the drivers to the previous version, but I'm not sure if thats gonna fix the problem.

---

### Post by #&amp;thj^% on 2023-10-13
This appears to be one issue " https://apt.repos.intel.com/oneapi/dists/all/InRelease"
This is what I see:
```
<Error>
<Code>NoSuchKey</Code>
<Message>The specified key does not exist.</Message>
<Key>oneapi</Key>
<RequestId>F0SS7PB13VFSEWAZ</RequestId>
<HostId>
/x+S8kHWRpHrtZCMCcE4vGUkd0tHnSHJLAY8VNWPNrjyCr9Xc6X0KyirHYYcyCY7VrHkmWoI5qY=
</HostId>
</Error>
```
Remove that from your sources and try again.

---

