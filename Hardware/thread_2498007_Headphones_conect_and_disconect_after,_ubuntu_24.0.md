---
title: "Headphones conect and disconect after, ubuntu 24.04"
date: 2024-05-25
forum: Hardware
---

### Post by gleystonbm on 2024-05-25
So, It's not a new problem, at least for me. The only upgrade that I managed to make my USB cheap dongle Bluetooth to work properly was in 22.04, for a brief period of time. But new upgrade new and quickly broken hope. what's precisely happens, I have a cheap cambrige silicon radio USB Bluetooth, works like a charm in windows, but in Ubuntu, you already know the story. Already tried every fix that I could find on internet, from the basics, sudo apt update and then sudo apt upgrade, to editing Bluetooth configuration files in nano, change pulse audio for pipewire, installing the Bluetooth plugins, did the live logs one time to see whats the error, nothing that I could find an answer for. When I connect my earbuds, I have two different pairs of XIAOMIs, one REDMI2 and the other MI AIR 2 SE, for both same thing happens, I connect them, the system says its connected, but the earbuds wont appear in sound configurations, soon after they disconnect themselves and I go back to square one. Someone found, some, any, solution for this? anything i could try? I'm an intermediary user, i know the basics of terminal, basically copy and paste codes and se if they work. So I ask for whom want to help to have a little patience. I'm also new in the forum, so I apologize for any mistakes regarding categories or other things.

---

### Post by currentshaft on 2024-05-26
op

---

### Post by gleystonbm on 2024-05-26
I have builtin wifi on my notebook but i usually use cable to connect to the internet.
The result of the command that you had asked for: ~$ iwlist channel | grep Current 
lo        no frequency information.

enp3s0f2  no frequency information.

---

### Post by currentshaft on 2024-06-01
If this happens on Ethernet, I'm not sure what else it could be.

Check out this thread, a user is reporting similar issues: [https://ubuntuforums.org/showthread.php?t=2498113](https://ubuntuforums.org/showthread.php?t=2498113)

---

