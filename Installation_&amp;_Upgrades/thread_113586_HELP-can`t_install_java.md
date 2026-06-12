---
title: "HELP-can`t install java"
date: 2006-01-06
forum: Installation &amp; Upgrades
---

### Post by makba018 on 2006-01-06
hello
I get to step number 5 of the java installation package and then it says:

`Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type'

chmod +x jre-1_5_0_04-linux-i586.bin`

What does this mean? Where do find the command line? I also do not understand step number 6 which says:

''To install JRE, run the downloaded file. Type

fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin

dpkg -i sun-j2re1.5_1.5.0+update04_i386.deb''

How do i run the program, where do i type these lines.

Thanks for anybody's help, as i am a begginner at this.

Mokhtar, Ottawa, Canada

---

### Post by jeepmanjr on 2006-01-06
Check out:

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

This should pretty much take care of most of your problems.

There are several ways to get J2RE, including "sudo apt-get install app" and the GUI that came with your distro to access the repositories.  You probably need to investigate "universe - multiverse".

If ya just gotta do it by hand try to find a .deb file. Save it, open a terminal window and cd to where you saved the file.  Type "dpkg -i filename.deb" on the command line without the quotes and hit enter.  You may have to sudo first, I don't remember.

Google up my friend...There's lots to learn.

---

### Post by Luke771 on 2006-01-07
You type your commands in the terminal; that's menu-applications-accessories-terminal.
You can skip all the java (and a lot of other stuff) installing problems by using Automatix. Search the forums for it, you will get a command line that installs Automatix ...automatically :-) then you run the program from the System Tools menu and you get a GUI with a list of popular applications, including Jre 1.5.o.whatever and Sdk 1.5.something, you select what you want to install, hit OK (or Apply, or something like that) and that's it, you get your java and all the stuff you selected installed and ready to go. I think Automatix is man's greatest invention after beer.

---

