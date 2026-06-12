---
title: "creating a higher level user for the GUI?"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by weaslesripmyflesh on 2008-12-24
I need to create a user account with near admin permissions. Right now I can't change video drivers or even install ndswrapper. Actually it wont even let me do a hardware test.

How can I create an account with enough permission to do these things in the GUI.

---

### Post by upchucky on 2008-12-24
by default for the user's protection it is set up to not do what you are trying to do, but some things can be done with the right programs added. 

sudo on the command line is the better way of administrating.

---

### Post by weaslesripmyflesh on 2008-12-24
Yeah but I want higher permissions in the GUI.

---

### Post by Skripka on 2008-12-24
> **weaslesripmyflesh said:**
> Yeah but I want higher permissions in the GUI.

Any commands which need higher level privileges are prefaced with 'sudo'.  This is the super-user command-that gives literal "super-user" privileges to any command it is attached to.  There is NO need to create a separate account.  Sudo is as high as it gets.  Any command that is sudo has full write permissions to every file and folder on the drive.

If it is a graphical command you are using such as needing admin rights to change Nvidia-settings you would instead use 'gksudo'.

---

### Post by upchucky on 2008-12-24
> **upchucky said:**
> by default for the user's protection it is set up to not do what you are trying to do, but some things can be done with the right programs added. 

sudo on the command line is the better way of administrating.

sorry i did not make this clear enough. some things can be done with the right programs installed.

you are gonna have to look through the hundreds of available free software packages to find ones that can do whatever it is you are specifically trying to do. or post what it is you are specifically trying to do and someone may be able to tell you which package can do it, or if what ever you want to do can be done by a specific gui program.

---

### Post by weaslesripmyflesh on 2008-12-24
That is for use "in the GUI" not "on the GUI". I can't even install anything or open a pen drive to look at it's contents.

Seems like one should be able to access admin rights or near admin rights in the GUI somehow.

---

### Post by weaslesripmyflesh on 2008-12-24
> **upchucky said:**
> sorry i did not make this clear enough. some things can be done with the right programs installed.

you are gonna have to look through the hundreds of available free software packages to find ones that can do whatever it is you are specifically trying to do. or post what it is you are specifically trying to do and someone may be able to tell you which package can do it, or if what ever you want to do can be done by a specific gui program.

Just to be clear here, I can't look at the contents of a pen drive. I want to do things that I have the software to do but I can't use the software because I don't have permission to. 

I am doing all of this on my own machine of course so I should have permission to do at least simple things but I don't.

---

### Post by weaslesripmyflesh on 2008-12-24
Oh and to make my difficulties clearer, I am on a dual boot and what i am trying to install in Ubuntu is ndiswrapper so I can install drivers and have an internet connection. This means everytime something doesn't work I need to change over to windows until I think I have an answer then change back to Ubuntu to give it a try.

---

### Post by upchucky on 2008-12-24
you need to use sudo to give yourself rights to do read write drives files and such, otherwise anyone can do what you are wanting to do and totally hose the system by accident. this is the way it works, and if you try to understand you will appreciate it when it all makes sense. anyone that has hosed a windows machine wishes there was a system in place to stop them from their own evil accidents.

There is a learning curve here, it is not that hard but if you are patient and really want control of your pc stick it out and learn to edit and administer instead of point and click.

Please dont be put off, many years ago i was more ignorant than i am now, but now i love tinkering with linux.

---

### Post by weaslesripmyflesh on 2008-12-24
please read my new thread upchucky. It asks the question why are there GUI apps in the GUI that I can't use and why were they put there if they can't be used in the GUI.

I think you might missunderstand my problem.

---

### Post by upchucky on 2008-12-24
you may want to search for chmod

search for ndiswrapper

if you tried ubuntu with a live cd, did the live cd work with the net active? cause if it did while using the live cd , therein lies your answer to gettin the net to work on the hard-drive install. there will be a file on the live cd that has the net info the harddrive install needs.

---

