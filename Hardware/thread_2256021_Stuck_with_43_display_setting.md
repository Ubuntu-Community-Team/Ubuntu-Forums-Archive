---
title: "Stuck with 4:3 display setting"
date: 2014-12-09
forum: Hardware
---

### Post by rbscairns on 2014-12-09
I recently fitted a new display to my ASUS eee B202 (Ubuntu 14.04). My previous display was 1024x768. My new display is 1366x768.

When I go into Settings/Displays, the only resolution that I have available for selection is 1024x762 (4:3). I tried Detect Displays, but this returned "Unknown Display".

1024x762 does not look good on a 1366x768 display. how can I get an option to set my new display to 1366x768?

[ATTACH=CONFIG]258470[/ATTACH]

---

### Post by ibjsb4 on 2014-12-10
Does the option exists in xrandr?
```
xrandr
```
[https://wiki.ubuntu.com/X/Config/Resolution#Dynamically_testing_different_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Dynamically_testing_different_resolutions)

if not
[https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

ps:
I am impressed that your atom handles Unity.  Are you doing this on one gig of ram?

---

### Post by rbscairns on 2014-12-12
> **ibjsb4 said:**
> Does the option exists in xrandr?
```
xrandr
```
[https://wiki.ubuntu.com/X/Config/Resolution#Dynamically_testing_different_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Dynamically_testing_different_resolutions)

if not
[https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

ps:
I am impressed that your atom handles Unity.  Are you doing this on one gig of ram?

ibjsb4, thank you for your assistance. My eee B202 with the Atom and 1GB of RAM handles Unity without a problem.

Now, back to my problem. xrabdr returned:

[CENTER][ATTACH=CONFIG]258525[/ATTACH][/CENTER]

So my 1366x768 resolution is not currently available. I then started following the "Adding Undetected Resolutiolns" instructions. All went well (using gtf).

[CENTER][ATTACH=CONFIG]258526[/ATTACH][/CENTER]

Note that I wanted a resolution of 1366x768, however xrandr decided to make it 1368x768. Now I will try and work through a process of making this new resolution permanent at login for all users.

I am using a VGA input into my monitor from my B202 PC, hence i used VGA1.

---

