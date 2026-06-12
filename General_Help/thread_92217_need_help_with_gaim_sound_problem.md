---
title: "need help with gaim sound problem"
date: 2005-11-19
forum: General Help
---

### Post by onesojourner on 2005-11-19
My sound in gaim stopped working. I think the problem might be with alsa. I just need to set it to defaults again, I think.


[QUOTE=kruz][http://gaim.sourceforge.net/faq.php#q24](http://gaim.sourceforge.net/faq.php#q24)

and 

[http://gaim.sourceforge.net/faq.php#q23](http://gaim.sourceforge.net/faq.php#q23)

possibly installing another sound driver
or xmms could have messed it up
i had to set it back to alsa after i installed xmms

am i sure why ? no lol

also other sounds on the os and mp3/wave files work right?[/QUOTE]
 
    If you choose "Automatic", "ESD", or "Arts", Gaim uses libao to play sounds. Choosing "ESD" or "Arts" forces libao to play sounds using that method, while choosing "Automatic" lets it decide for itself.

    If you choose "Automatic", you can create a file, either /etc/libao.conf or ~/.libao, and put one of the following lines in it:

default_driver=alsa
default_driver=oss



basicly those sites say I need to enable alsa. I just don't really understand what the instructions mean. I need them to be a little more step by step. where do I type the commands?

---

### Post by mykey on 2005-11-19
Create a new file with your favorite editor (e.g. gedit) in your home directory and put in 'default_driver=alsa' - then save it as '.libao' - if this does not give you your sound back try another driver - change the 'alsa' to 'oss' in the file. 

NOTE - After you saved it you will not be able to see the file in Nautilus since linux hides files that start with a '.' in front - press 'Ctrl+h' to make those files visible in the file manager.

good luck

---

### Post by onesojourner on 2005-11-26
Just wanted to let you guys know I could not get this to work even with all the help. I just uninstalled it and reinstalled it and that took care of the problem.

---

