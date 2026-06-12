---
title: "my laptop crashes when I use backspace"
date: 2008-07-28
forum: Hardware
---

### Post by Mengus on 2008-07-28
Hello. I just installed ubuntu on my LW70 express Laptop.
everything seems to work except that it crashes if I press backspace several times after each other. This is anoying when editing text. 

I am running Linux 2.6.24-19.

please help.

---

### Post by overdrank on 2008-07-28
> **Mengus said:**
> Hello. I just installed ubuntu on my LW70 express Laptop.
everything seems to work except that it crashes if I press backspace several times after each other. This is anoying when editing text. 

I am running Linux 2.6.24-19.

please help.

Hi and when you mean crash, does the system bring you to the login screen?
Like if you restart x with the ctrl, alt, backspace keys.

---

### Post by Mengus on 2008-07-28
no. I mean crash. the whole system hangs and I have to reboot by turning of computer. I have now noticed the same goes for the delete button and tab.

---

### Post by zenum on 2008-08-24
I have an Lw60 and I've been starting to have that problem recently as well, it's quite bizzare. Normally when the computer crashes it's been some kernal panic, but there is no output of any errors.
Memory is fine, I ran memcheck overnight with no errors, I've tried different hard disks, different distributions.
It crashes using ubunutu, opensuse and backtrack which are the 3 I tried.
It doesn't cause any problems in Windows though so it's a bit weird...

I even had a look at the cabling of the keyboard and it seems to be fitted in quite nicely...

If there is no solution, could someone direct me in a way to at least determine the problem? Is there some sort of logging I could do to capture the possible error?

---

### Post by zenum on 2008-08-25
Hi, I tried disabling ACPI (acpi=off) and so far my laptop hasn't crashed. All day yesterday I tried various different things and I could replicate the crash by simply backspacing on the command prompt just after logging in. Today after disabling acpi I tried the same thing and it didn't freeze.
Unfortunately I need acpi otherwise my laptop doesn't know it has a battery to worry about... so the trick now will be to find out why acpi is causing my laptop to crash, and getting it fixed!

I'll keep digging around, hopefully this post helps other people looking for an answer.

---

### Post by jalupinja on 2008-10-08
I had this same prob, it seems that it has something to do with the sound card not being detected?

system/preferences/sound...click on system beep!!! Uncheck system beep, if you prefer you can enable visual beep which flashes the screen or menu bar, whichever you select.

No more lock up....yay!!! Now if someone knows how to get sound enabled please drop me a line....I'm on week three and still..."no sound device found"...c-media 9880!

---

### Post by Mengus on 2009-02-20
yes. just found out yesterday that it was the PC speaker that causes the freeze. Beware that turning it of in the system menu does not solve the whole problem. The System Beep is also invoked under the terminal without any running X server or gnome. To fix it completely you need to blacklist pcspkr. This is how you do it:

1. Open file "/etc/modprobe.d/blacklist" as root with your prefered editor
2. Navigate to the end and add the following lines:

#Blacklist PC-Speaker
blacklist pcspkr

3. Save the file and reboot

I was stuck with this problem for months! and thats how easy it could be fixed(assuming one can live happily without the System Beep :)).
I hope this will help someone with the same problem.

---

### Post by SciB6y on 2009-04-20
Update for peoples with 9.04 (Jaunty Jackalope) is that the "blacklist"-file is nowadays called "blacklist.conf". It is the same file, just a new name (I'm guessing that they are making the configuration files more consistently named so that it is possible to know which files are what).

---

