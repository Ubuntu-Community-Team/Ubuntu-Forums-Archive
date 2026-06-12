---
title: "Absolute beginner - how do I install from a tar.gz file"
date: 2008-09-18
forum: General Help
---

### Post by michael@cgl on 2008-09-18
I have extracted a folder from a tar.gz file, which I believe has the install files that I need.

how do I install this package ? 

I am an ex windows admin and have migrated gratefully to ubuntu. trying to get whole workplace to migrate. Feel sick when I remember XP . . . :-)

---

### Post by whizbaby on 2008-09-18
Welcome to rehabilitation then ;)
It depends actually on what was inside the tar.gz
Is there sourcecode? Then you would need to compile.
Is there a .deb file? Then give
```
sudo dpkg -i nameofthefile.deb
```
a try. Just ask if you need further info.

---

### Post by MegaJim on 2008-09-18
That depends on what is inside it, source code, binary, bytecode, package etc. (.tar.gz is just an archive)... where did you get it from/what is it?

---

### Post by michael@cgl on 2008-09-18
cant find a .deb or a .rpm file, though that doesnt mean they arent there.

its magento, an open source ecommerce package. I just want to try it out. 

there is an install.php file, but im not sure if php is installed on this ubuntu machine

how do I check if php is there ? (Absolute beginner, with an advanced dose of XP-itis)

michael

---

### Post by anotherdisciple on 2008-09-18
What is the program that you are trying to install... there is a good chance that it is in the repositories, or that you can add a repository.

---

### Post by whizbaby on 2008-09-18
Please post the output of
```
cat install.php
```
so we can see what it is (maybe its the installer, dont think it will install php). As far as I know php is installed per default. But you can check installed packages with
```
dpkg -l
```
but this will give you a rather long list, so you can filter the output with grep
```
dpkg -l|grep php
```
(yes, thats a 'pipe', a vertical line, not 'l' or '1')
This will give you a list of packages that have php in their name, 'ii' at the beginning of a line means 'installed'.

---

### Post by karlr42 on 2008-09-18
"how do I install from a tar.gz file"?
**Don't**, if you can possibly avoid it. In Linux, unlike Windows, you *don't get software by getting install files over the net.* *You use repositories*, huge collections of software that's easy to install and is compatible with your OS, guaranteed. 
Go System->Administration->Synaptics Package Manager. You can see a list of all that software. To see more(which you probably will have to), go Settings->Repositories and tick all the unticked boxes in the first tab. Then search for the program you want, magneto.
AS it happens, that program is not in the repositories, but next time you want a certain program, **use Synaptic!** Trust me, you'll love it

---

### Post by SeanHodges on 2008-09-18
It appears Magento is a Website. That .tar.gz file is just a "zip" archive containing all the web pages and various other files it needs. 

You will first need to install Apache, MySQL, and PHP to use it, follow these instructions:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Then extract the archive into your /var/www directory.

Once you've done that, you will need to set up MySQL for Magento and make sure the file permissions are correct, as described by the instructions on the website:

[http://www.magentocommerce.com/wiki/magento_installation_guide](http://www.magentocommerce.com/wiki/magento_installation_guide)


Edit: Also, Magento is not in the repositories, so you will need to use the tar.gz version you have there.

---

### Post by michael@cgl on 2008-09-18
thanks guys.

php doesnt seem to be there, and thanks for the ii. I wondered what they meant. 

installing those things . . .   :-)

also:

michael@michael-desktop:~$ cat install.php
cat: install.php: No such file or directory

also, how do I install from that extracted magento folder ?

---

### Post by mb_webguy on 2008-09-18
You need to install Apache and PHP.  Open Synaptic, and go to Edit->Mark Packages by Task.  Check the box next to LAMP server, then click the Apply button to install the packages.  Now if you open your web browser and type "localhost" in the address bar, you should see a page that says something like "It Works!!!".

The default Apache web root is /var/www, so that's where you need to put the extracted Magento folder, but first you need to clean it out so you don't just see that stupid "It Works!!!" page.  I think /var/www is only writable by root, so open the terminal and type "sudo rm -r /var/www/*" to remove all of Apache's default web files.  Trust me, you don't need them.  Now type "sudo mv /path/to/magento /var/www/magento".

Now if you reload the "localhost" page in your browser, you should see a directory listing of the /var/www folder, containing the magento folder.  Click on the magento folder to open the magento web site you just installed.

---

### Post by Zyphrexi on 2008-09-18
wow... impressive.


also there's absolutely nothing wrong with installing programs from .tar.gz archives. I use ubuntu because of the repos, but some programs don't exist in any repositories. In that case it's usually source and I just build it.

EDIT: also being that the OP is a former windows admin, it's probably better that he/she learns more about the OS itself, that and linux/unix sysadmins get paid way more. (job security ftw!!!)

---

### Post by mb_webguy on 2008-09-18
True, but being a former sysadmin, I'm sure the OP knows the risks associated in running unverified code.  Software in the repositories or in trusted PPAs has the advantage of some degree of verification to make sure that it doesn't contain malicious code.  There are no such assurances associated with compiling an application from source.

And while you assume the same degree of risk by installing software using a deb downloaded from the Internet, at least it's easier and less time-consuming than installing from source.

---

### Post by michael@cgl on 2008-09-19
thankyou very much



- exwindows sufferer - I nearly died :)

mick

How do I change to root, in order to get privelages to move the magento folder to that www folder ? Ive tried su at the console and it doesnt seem to like the password, which I thought was the same as my password automatically when ubuntu was installed

---

### Post by fsmithred on 2008-09-19
Ubuntu doesn't have a root account, but your main user should have admin privs by preceding commands with 'sudo'. If you want a root terminal for longer than a few minutes and don't want to type 'sudo' before every command, you can do 'sudo -i' and then you'll be root until you close the terminal. If you like playing with weaopns of mass destruction, you can do 'gksudo nautilus'.

---

### Post by Zyphrexi on 2008-09-20
I recommend playing around with a junk computer. I'm sure you have plenty. Ubuntu probably isn't the best distro for that though, but once you get to the point where you feel comfortable with linux, using other distros shouldn't be a problem.

for root stuff, I always did sudo su
that's  probably the same as sudo -i I suppose.

---

### Post by mb_webguy on 2008-09-20
You can also use "sudo bash" to open a bash shell as root.

---

### Post by cacycleworks on 2009-01-07
You might find this useful:
sudo chown -R www-data:www-data magento

:)

Other really handy website commands (prolly need to be sudo):
find ./papers/ -R -type d -perm 755 -print0 | xargs -0 chmod 775
find ./papers/* -R -type f -perm 644 -print0 | xargs -0 chmod 664

which work this way, too:
find ./papers/  -type d -print0 | xargs -0 chmod 775
find . -type f -print0 | xargs -0 chmod 664

These above find's will realign permissions so that a web app can better play with the files. OR you can get sly and chmod so that the group is your username group...
sudo chown -R www-data:chris magento
... and with 775, you can play around in there all you want and maybe not need to sudo so much.

etc etc etc... 
And before you ever do this to a directory... best to:
tar -czvf backup.tgz papers/

:) Chris

ps - magento installs VERY nicely compared to other "things" I've tried. Now to finger out how to use Zend Studio with it. :P

---

