---
title: "GIMP upgrade failure"
date: 2008-11-04
forum: General Help
---

### Post by Mohamedzv2 on 2008-11-04
So when I open GIMP after I updated it to 2.6, I get this message "There was an error parsing the menu definition from toolbox-menu.xml: Failed to open file '/usr/share/gimp/2.0/menus/toolbox-menu.xml': No such file or directory"

So when I went to teh Add/Remove apllications this happens:
"Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

I just started using Ubuntu a few days ago, haven't used a linux before, what should I do?

---

### Post by taurus on 2008-11-04
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get install -f
sudo apt-get update
```

---

### Post by Mohamedzv2 on 2008-11-04
So now that I've done that, how do I get back GIMP?

---

### Post by taurus on 2008-11-04
What happens if you run it from a terminal, any error message?

```
gimp
```
And how did you upgrade it to version 2.6?

---

### Post by ajgreeny on 2008-11-04
I know it can work as I have done it already on an install of Mint 5.  I downloaded the six files from [getdeb]("http://www.getdeb.net/"), put them in a temporary folder (Gimp_Packages) in home and then used ```
cd Gimp_Packages && sudo dpkg -i *.deb
```It worked without a single problem.

---

### Post by Mohamedzv2 on 2008-11-04
I installed the bzu from the gimp.org's ftp.

And when I try to run it, it says, "The program 'gimp' is currently not installed.  You can install it by typing:
sudo apt-get install gimp"

then when I type to install it "he following packages have unmet dependencies:
  gimp: Depends: gimp-data (< 2.4.5-z) but 2.6.2-1~getdeb1 is to be installed
E: Broken packages"

---

### Post by ajgreeny on 2008-11-04
See my post No. 5.  you need all the dependencies that are listed on the getdeb site if you want it to install properly.

---

