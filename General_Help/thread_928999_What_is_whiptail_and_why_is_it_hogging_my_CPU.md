---
title: "What is whiptail and why is it hogging my CPU?"
date: 2008-09-24
forum: General Help
---

### Post by Tsu Dho Nimh on 2008-09-24
Working with a new install of 32-bit Kubuntu Hardy Heron and something called "whiptail" is using 30+% of my CPU cycles.

What is it doing?

---

### Post by kostkon on 2008-09-24
> **Tsu Dho Nimh said:**
> Working with a new install of 32-bit Kubuntu Hardy Heron and something called "whiptail" is using 30+% of my CPU cycles.

What is it doing?
You must have installed something that uses it. Check [here]("http://packages.ubuntu.com/hardy/whiptail") to see what *whiptail* is all about.

It seems that somehow this script/app got started but never closed or killed. For example do a
```
ps -fu yourusername | grep whiptail
```
to get some more info about this process, i.e. when it started and it's path in your file system.

---

### Post by Tsu Dho Nimh on 2008-09-25
> **kostkon said:**
> You must have installed something that uses it. Check [here]("http://packages.ubuntu.com/hardy/whiptail") to see what *whiptail* is all about.

It seems that somehow this script/app got started but never closed or killed. For example do a
```
ps -fu yourusername | grep whiptail
```
to get some more info about this process, i.e. when it started and it's path in your file system.

It provides a method of displaying several different types of dialog boxes from shell scripts. This allows a developer of a script to interact with the user in a much friendlier manner.

OK ... I know I have installed shell scripts - Linux is crawling with them. Is there a way to see which of the bazillions of shell scripts that are installed have been written to use whiptail instead of ncurse? 

At the time it was eating up 30% of my CPU, I had no scripts open that I knew about.

---

