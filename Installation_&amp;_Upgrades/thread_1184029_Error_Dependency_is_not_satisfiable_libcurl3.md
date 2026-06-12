---
title: "Error: Dependency is not satisfiable: libcurl3"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by Ichinenjuu on 2009-06-10
I'm new to Linux; I just installed Ubuntu today, so I don't know anything. Sorry if I'm asking a stupid question. What does "Error: Dependency is not satisfiable: libcurl3" mean?

I was trying to install Adobe Flash Player and that's what came up.

What am I doing wrong?

---

### Post by ibutho on 2009-06-10
Hi and welcome to the forum. What exactly did you do (i.e. commands, actions you took etc) before getting the error message?

You could try the instructions [here]("https://help.ubuntu.com/community/RestrictedFormats/") for installing flash and other plugins.

---

### Post by Ichinenjuu on 2009-06-10
I did [B][Click here to install the ubuntu-restricted-extras package]("apt:ubuntu-restricted-extras?section=universe?section=multiverse")
and then tried installing it again, but I got a different error. I downloaded the plugin and clicked "Install Package" and then it says "could not download all required files" and the details say "Failed to lock /var/cache/apt/archives/lock". What's going on?
[/B]

---

### Post by bg26892 on 2009-06-12
> **ibutho said:**
> Hi and welcome to the forum. What exactly did you do (i.e. commands, actions you took etc) before getting the error message?

You could try the instructions [here]("https://help.ubuntu.com/community/RestrictedFormats/") for installing flash and other plugins.


This link on the page appears broken...
**[Click here to install the ubuntu-restricted-extras package]("apt:ubuntu-restricted-extras?section=universe?section=multiverse")**

---

### Post by ibutho on 2009-06-13
> **Ichinenjuu said:**
> I did [B][Click here to install the ubuntu-restricted-extras package]("apt:ubuntu-restricted-extras?section=universe?section=multiverse")
and then tried installing it again, but I got a different error. I downloaded the plugin and clicked "Install Package" and then it says "could not download all required files" and the details say "Failed to lock /var/cache/apt/archives/lock". What's going on?
[/B]
On the link I provided above, try the instructions for Ubuntu 8.10, 8.04 and 7.10. They should work even on 9.04.

---

### Post by Partyboi2 on 2009-06-13
> **Failed to lock /var/cache/apt/archives/lock**
Hi Ichinenjuu,
This happens when trying to use another package manager (gdebi apt-get, synaptic. update-manager) while one is already open. You can only have one one running at a time.

---

### Post by Razor338 on 2010-12-27
i used to get this error when installing limewire pro.The problem was i didn't download java runtime environment!

---

### Post by Razor338 on 2010-12-27
i used to get this error when installing limewire pro.The problem was i didn't download java runtime environment!

---

### Post by guntario on 2011-05-06
Thank you for mentioning that you need to install Java. This solved the problem. I installed Java runtime 6.

---

