---
title: "i installed opera web browser but now i cant find it/run it"
date: 2008-07-13
forum: General Help
---

### Post by eival on 2008-07-13
ive installed plenty of apps an programs before but Opera web browser seems to be the only one that gives me trouble.

ive tried installing the 2 ways i know how

first

i downloaded opera in TAR format, i unzipped the file, opened the terminal, an typed 

sudo apt-get install "then i drag the unzipped folder here"

hit enter, then put my password, press Y to continue install, an then it goes through the normal process of installing, with no error message at the end.

but i cant find the web browser in my Applications > INternet tab

i run a scan, nothing is found.

so then i try manually clicking on the Install file inside the unzipped folder, and tell it to RUn in Terminal, i again press Y to continue, it goes through the whole install, but i still dont see Opera

finally i tried just clicking the install file again and selecting RUn, but it never opens an i dont see it in my system processes.


is there another way to install that im not doing?

if someone with more installing knowlege could test this out an let me know how they got it to work id be greatly appreciative. :popcorn: 


im using Hardy Haron

---

### Post by perlluver on 2008-07-13
Just download the .deb file for Ubuntu 8.04 and double click it.  It will install and should show up in your internet tab.

Here is the link [Opera for Linux.]("http://www.opera.com/download/linux/")

---

### Post by rushikesh988 on 2008-07-13
ya thats it !!

---

### Post by mexpolk on 2008-07-13
Another way to do so, is by command line:

1. Download your .deb package.
2. Install it:

```

$ sudo dpkg -i your_package_name.deb

```

Note: Some times you don't have all the required dependencies to install it. So your installation will fail. If that's the case run the following:

```

$ sudo apt-get install -f

```

And it will install the dependencies and your .deb package.

best!

---

### Post by eival on 2008-07-14
> **perlluver said:**
> Just download the .deb file for Ubuntu 8.04 and double click it.  It will install and should show up in your internet tab.

Here is the link [Opera for Linux.]("http://www.opera.com/download/linux/")

okay, ill try this out

---

### Post by eival on 2008-07-14
the double click worked fine, i cant believe ive been doing things the hard way all this time :lolflag:

thanks for the help :guitar:

---

### Post by eival on 2008-07-15
okay, now i have a new problem i want to install an older version of the browser, so i ran this through the terminal

sudo apt-get remove opera

i got no errors, and Opera was removed from my Internet tab, it was gone.

and i know it was removed cause when i tried to install an older version of opera it didnt give me the "theres already a newer version installed" error.

so then i downloaded 9.27 from opera.com and installed the deb file like above but when it finished and i opened Opera it was still version 9.5 with all my bookmakrs an saved passwords and preferences???

is there some sort of autoupdate thats in the ubuntu version?

cause the windows version never autoupdated, you had to manually download the new version, install an even then it would ask if you wanted to do a seperate install or install over the current version keeping your settings.

---

