---
title: "mount WD My Book World drive"
date: 2015-01-02
forum: Hardware
---

### Post by andrew185 on 2015-01-02
My WD My Book World drive has crapped out on me.  I took the hard drive  out of the case and put it into my desktop.  I am now trying to access  the drive with the only purpose of recovering famly pictures. I am completly new to computers. ( the last time i tried to learn about computers dos for dummies was my go to) any help will be greatly appreciated. i did find one old post with the same problem but no solution, i'm hoping one may have been found since then.

---

### Post by Irrationalis on 2015-01-02
Open up a terminal emulator:
go to "Dash Home" on the sidebar, and search for "Terminal"

Then type
```
sudo fdisk -l
```

You will have to enter your password.
Note: no characters will be display at the prompt in order to protect your password from prying eyes.

Please paste the output of the command in code tags:
click "**Go Advanced**" at the bottom of the reply box, and use the *"#" *button in the editor toolbar.

---

### Post by Bucky Ball on 2015-01-02
What flavour and release of Ubuntu are you using?

---

### Post by yancek on 2015-01-02
The first thing you need to check is whether it is recognized in the BIOS.  If not, you don't have much hope for recovering anything.

---

