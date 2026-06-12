---
title: "Using package manager"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by CarlSeiler on 2009-06-03
This week, after having used several other distributions and having difficulties with ease-of-use issues, I installed Xubuntu on my computer.  

I decided that I would like to check out MonoDevelop, so I used the synaptics package manager to install it and all dependencies.  It reported that it installed successfully, but now I can't find the software anywhere in the menus.  Under Development, only geany appears.  Do I have to manually add software to the menus if I want to be able to access them there?

---

### Post by oldos2er on 2009-06-03
Try typing **monodevelop** in a terminal.

---

### Post by CarlSeiler on 2009-06-03
> **oldos2er said:**
> Try typing **monodevelop** in a terminal.
Hmmm.

It says:  "The program 'monodevelop' is currently not installed.  You can install it by typing:..."

So, I guess it was not successful in installing.  After some poking around, I find that what I installed with synaptic package manager is something called mono-devel, not monodevelop.  I was attracted to mono-devel  by the fancy little ubuntu logo next to it in the list.  monodevelop package is missing that, and my eye just wasn't drawn to it, and afterwards, I thought I'd installed but hadn't.

Thanks

---

### Post by directhex on 2009-06-03
> **CarlSeiler said:**
> Hmmm.

It says:  "The program 'monodevelop' is currently not installed.  You can install it by typing:..."

So, I guess it was not successful in installing.  After some poking around, I find that what I installed with synaptic package manager is something called mono-devel, not monodevelop.  I was attracted to mono-devel  by the fancy little ubuntu logo next to it in the list.  monodevelop package is missing that, and my eye just wasn't drawn to it, and afterwards, I thought I'd installed but hadn't.

Thanks

The logo basically refers to whose responsibility a package is - it means that Canonical staff will issue security updates for the package, as opposed to community best-effort for logo-free packages. For companies, this is important.

mono-devel is required for compiling Mono-related packages, and since Mono is paer of a default Ubuntu install, it gets a logo. The MonoDevelop IDE is not part of a default anything, and is a community-supported package

---

