---
title: "Building a new PC and I want to be sure it will be compatible with 14.04"
date: 2016-03-17
forum: Hardware
---

### Post by Andi_GreyScale on 2016-03-17
Here's the list of parts: [http://pcpartpicker.com/user/AndiGreyScale/saved/b7F7YJ](http://pcpartpicker.com/user/AndiGreyScale/saved/b7F7YJ)

The programs I use are already all compatible (using them now) so that wont be an issue. 

I'll be waiting a couple months before upgrading to 16.04 as well. =)

---

### Post by RobGoss on 2016-03-17
Hello and welcome, Ubuntu will run on just about anything that has a connection, meaning it does not take much to run any of their distributions

Here's list of what needed to get Ubuntu up and running

Installation / SystemRequirements Ubuntu
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Keep in mind if Ubuntu runs with less resources that means the better the specs are for your machine Ubuntu will be faster them anything you'e ever seen.

---

### Post by buzzingrobot on 2016-03-18
I have a 750ti card.  Until recently, it as essentially unusable with the Nouveau driver. (Nouveau is the open source driver for Nvidia cards.  It is used by default when an Nvidia card is the active video card when a system boots.) I recommend installing the current 14.04.04 release which has a newer kernel and video stack: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

The nvidia-352 proprietary driver available in the repos for Trusty works well here. That can be installed via the "Additional Drivers" tool.

---

