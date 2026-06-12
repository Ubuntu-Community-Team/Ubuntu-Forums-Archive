---
title: "Synaptic No Longer Working"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by measekite on 2009-02-28
I am still using Feisty 7.04 by choice and cannot change for at least another month since I am in the middle of a project.

I can not longer get applications using Synaptic.  It does not matter which ones.  When I select one and choose apply I get a dialog that with a drop down that says **Not Authenticated** and if I still go ahead I get a bunch of errors.

[SIZE=3][COLOR=Red]Is there any way to correct this?[/COLOR][/SIZE]

---

### Post by taurus on 2009-02-28
It's because the release has been expired and the repos have moved.

Therefore, you need to edit your /etc/apt/sources.list

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
gksudo gedit /etc/apt/sources.list
```
and replace your current repos, something like

```
deb http://us.archive.ubuntu.com/ubuntu/
```
to
```
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)
```
Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

---

### Post by measekite on 2009-03-01
> **taurus said:**
> It's because the release has been expired and the repos have moved.

Therefore, you need to edit your /etc/apt/sources.list

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
gksudo gedit /etc/apt/sources.list
```and replace your current repos, something like

```
deb http://us.archive.ubuntu.com/ubuntu/
```to
```
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)
```Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

This worked but for me to make it work in Synaptic I had to open Synaptic snf fo s [B]reload.

Thanks very much.

[/B]I do have one question.  Instead of getting an error that just says Not Authenticated why could there have been a notice similar to what you said with the suggestion to do what you wrote.  It would seem that would be the way to handle something like this.  Or better yet a button in Synaptic that would do this for you or even have it on the Settings menu as a choice.

---

### Post by measekite on 2009-03-06
> **taurus said:**
> It's because the release has been expired and the repos have moved.

Therefore, you need to edit your /etc/apt/sources.list

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
gksudo gedit /etc/apt/sources.list
```
and replace your current repos, something like

```
deb http://us.archive.ubuntu.com/ubuntu/
```
to
```
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)
```
Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)
Thanks for the help.  It worked fine.

---

