---
title: "Zenbook UX305CA live session"
date: 2016-06-09
forum: Hardware
---

### Post by ole8 on 2016-06-09
Hi,
I run into a puzzling problem with my Zenbook UX305CA (Skylake M7-6Y75). I am trying to get a USB live session to work so that I can install Ubuntu (Gnome flavor). This is difficult with the current LTS, but I can get into the live session either by configuring the GRUB of Xenial (with flags like nomodeset), or by using the current build of Yakkety. Even the touchpad often works from the start.

However, nothing else works. I cannot start any application, open a terminal, open Settings or anything else. I also cannot start an installation. When I click on an application, it sometimes looks like it is opening (the name shows up in the upper bar), but nothing happens. Sometimes, I get the error message: "Failed to execute child process [name]. Input/output error." The screen doesn't freeze and there is no kernel panic, I just can't do anything. Shutdown also doesn't work.

It's always the same problem, in Xenial (both standard and Gnome flavor), Yakkety build, and also Fedora 23. I always get into the live session and no further. 

There is a lot of help online about how to get the touchpad, graphics etc to work on the Zenbook UX305CA, but I could not find anything specific on this problem. Any help is very much appreciated. I have thought about trying more complex solutions (putting a newer mainline kernel on a customized live USB?), but as long as I don't really understand why the problem occurs that doesn't seem to be very promising.

---

