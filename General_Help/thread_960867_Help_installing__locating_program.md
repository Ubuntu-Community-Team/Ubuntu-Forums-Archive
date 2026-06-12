---
title: "Help installing / locating program"
date: 2008-10-27
forum: General Help
---

### Post by mnelson07 on 2008-10-27
Hi, I just decided to switch to Ubuntu from using Windows for the past eight years and so far it's been both good and bad.

First off, I understand that it is easiest to install programs via the Synaptic Package Manager, and it worked great for installing AWN. However, I tried to install Synergy and Conky via SPM and it seemed to have installed but I can't find the programs listed anywhere (AWN put a shortcut in Applications > Accessories). I also tried installing them via the Terminal and it says it was installed but still nothing. I read before someone say something about installing the necessary multiverse and universe files. How do I find them/check to see if I have them?

Lastly, how can I have some of the programs (like conky [if I can get it installed] and AWN) startup when I log in?

I've done some searching through the forums before I posted this, so if I did overlook something you're welcome to just post a link to the answer rather than taking the time to type it out.

Thank you for your time!

---

### Post by unutbu on 2008-10-27
Hi mnelson07, welcome to the ubuntuforums.

In Synapic, right-click on the package that you installed (such as conky.)
Select Properties
Click on the Installed Files tab.
There you will see all the files that got installed on your system (and where).
Typically, executables get installed in a directory called "bin".
In the case of conky, the executable is installed as /usr/bin/conky.

Conky is one of many programs that does not place itself in your Applications menu.
To get it to run at when you log in, go to System>Preferences>Sessions and add it to the list of programs.

By googling around you may discover that there is a sample conkyrc file that gets installed along with conky: /usr/share/doc/conky/examples/conkyrc.sample.gz
Copy the text to ~/.conkyrc, and then edit it to suit your taste.
You might also want to check out [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)
for ideas on how to setup your conkyrc.
> 
I read before someone say something about installing the necessary multiverse and universe files. How do I find them/check to see if I have them?

Go to System>Administration>Software Sources.
Under the first tab, "Ubuntu Software", make sure the "...(universe)" and "...(multiverse)" check boxes are enabled.

---

