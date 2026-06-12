---
title: "Newbie Here (Yay Linux) Question..."
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by TheSlav on 2009-03-11
Hello everyone, Using Linux for the first time. Just wondering if there are any tweaks that you guys could tell me about to make ubuntu leet haha, even though it already is :). I'm on Ubuntu Intrepid 8.10 or something or other.

---

### Post by marsdend on 2009-03-11
Just search through the add/remove, tons of software and addons!

Also, check out gnomelook.org for themes, boot screens etc

---

### Post by Neo_The_User on 2009-03-11
Compile a custom kernel under 700K and set the timing frequency to 1000 Hz and set the "processor and type" to the CPU that you use. Your system will boot up quicker and screaming fast. Also, installing the restricted drivers for your GPU would speed things up as well. Keep in mind that if you are new to linux compiling a custom kernel would not be the first best thing for you to do. Start out with the drivers and work your way up from there. xorg.conf optimization for compiz etc etc. When I first started using linux about 3 years ago, the first thing I did was dig through the documentation and source code of my everyday applications to see how the structure of linux is built. Somebody is probably going to read the first sentence of this post and be like, "Neo... just stop. seriously. You're not helping." Well, the docs explain most of it.

1 more thing, if you are  going to use an application that doesn't look graphical at all, you can open it up in the terminal, located in Applications > Accessories > Terminal and type in this command without parenthesis:

```

man (package)

```

The name of the package goes where it says "(package)" except don't use parenthesis. You can then use the up and down arrows to browse through the help of the command line application. Command line means Terminal (cli)

---

### Post by TheSlav on 2009-03-12
Thanks Neo, I really appreciate it :). Although I'm gonna have to translate everything you just said into lamen ( however it's spelt) terms haha. Cheers.

---

### Post by konqueror7 on 2009-03-12
you could try installing [Ubuntu Tweak]("http://ubuntu-tweak.com/") if you want...:D

---

### Post by archer6 on 2009-03-12
Welcome to the forum!
.
I agree with the others suggestions. To which I might suggest, if your system is working properly now, leave it alone for awhile and enjoy it. 
.
While you have a working system, read all that you can about Ubuntu so as to prepare yourself. Then when you do the mods that appeal to you your success rate will be very good. 
.
Cheers...
.
Posted via BlackBerry

---

### Post by scphan on 2009-03-12
don't forget conky or compiz  "sudo apt-get install conky" in the terminal, also make a keyboard shortcut for the terminal (preferences>keyboard shortcuts), for compiz check out the add/remove apps. from the menu, compiz lets you have transparent windows and other cool desktop effects assuming your video drivers are up and running

---

