---
title: "Install Problem (plz help a noob)"
date: 2008-08-07
forum: General Help
---

### Post by ikxgamex on 2008-08-07
Hi. I've downloaded a Halo Stats Tracking tool and Cannot figure out how to install it. I've been able to install many things before, but for some reason this just isnt working the way it should, I'm getting all sorts of errors. Can anybody try to help me install this small program? 


[http://www.edchipman.ca/programs/files/hsaDE_linux.zip](http://www.edchipman.ca/programs/files/hsaDE_linux.zip)

---

### Post by loligager on 2008-08-07
do a "sudo apt-get install wine"
than try it
i am asuming it is a windows file and i am assuming you are able to extract it.

---

### Post by ikxgamex on 2008-08-08
I already have wine installed, and have even tried running the windows version, but with no luck. I type "sudo make install" in a terminal and I get a message saying that the "install.sh" file is copied, renamed to "install", and givin executable permissions. I then try running "install" or "sh install.sh" in the termainal, but nothing happens. Can someone please try to install this so that I know it actually works? =]

---

### Post by aaronanderson on 2008-08-08
Can you copy and paste the contents of your terminal when you run install.sh?

---

### Post by nagasuman on 2008-08-08
check this out. more stuff coming in here

[http://iweavers.blogspot.com](http://iweavers.blogspot.com)

:guitar:

---

### Post by ikxgamex on 2008-08-08
Yup. Here it is, all I am able to do. ```
ikgamex@ikgamex-ubuntu:~$ cd Desktop
ikgamex@ikgamex-ubuntu:~/Desktop$ cd halo
ikgamex@ikgamex-ubuntu:~/Desktop/halo$ sudo make install
[sudo] password for ikgamex: 
cat install.sh >install 
chmod a+x install
ikgamex@ikgamex-ubuntu:~/Desktop/halo$ sudo sh install.sh
install.sh: 13: Syntax error: end of file unexpected (expecting "fi")
ikgamex@ikgamex-ubuntu:~/Desktop/halo$ sudo bash install.sh
install.sh: line 14: syntax error: unexpected end of file
ikgamex@ikgamex-ubuntu:~/Desktop/halo$ sudo install
install: missing file operand
Try `install --help' for more information.
ikgamex@ikgamex-ubuntu:~/Desktop/halo$ 

```

What should I do next? If you downloaded the archive, you can see that I have very few files to work with. I tried opening "install.sh" with a text editor and individually running each command, but that didn't work too well either.

Here's what the install.sh script contains: ```
#!/bin/sh

if [ $(id -u) != "0" ]

    then echo "You must run this script as root" >&2

    exit 1

fi

apt-get --assume-yes install php5-cli php5 php5-gd php5-sqlite3 php5-sqlite libzzip-0-13;

cp ./packages/60_php-gtk2.ini /etc/php5/cli/conf.d

cp ./packages/php_gtk2.so /usr/lib/php5/20060613+lfs



cp ./packages/zip.ini /etc/php5/cli/conf.d

cp ./packages/zip.so /usr/lib/php5/20060613+lfs



php -f src/installer.phpw
```


I ran each of these individually, and everything seems to work fine until I run the php installer command at the end. Whenever I run that, I am greeted with: ```
ikgamex@ikgamex-ubuntu:~/Desktop/halo$ php -f src/installer.phpw
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php/extensions/php_gtk2.so' - /usr/lib/php/extensions/php_gtk2.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php/extensions/gd.so' - /usr/lib/php/extensions/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php/extensions/pdo.so' - /usr/lib/php/extensions/pdo.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php/extensions/pdo_sqlite.so' - /usr/lib/php/extensions/pdo_sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php/extensions/sqlite.so' - /usr/lib/php/extensions/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php/extensions/sqlite3.so' - /usr/lib/php/extensions/sqlite3.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php/extensions/zip.so' - /usr/lib/php/extensions/zip.so: cannot open shared object file: No such file or directory in Unknown on line 0
bcompiler v0.14s	&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Iconfig/constants.phpIconfig/main.phpcHSA_DESK_DIR_ROOT<(src/includes/installer.inc.phpIPs<	<d	php_uname		xLinux	#	cat /etc/lsb-release<
<&#65533;
shell_exec

```

Any Ideas?

---

### Post by aaronanderson on 2008-08-08
There's definitely a problem with the if statement, but I'm not sure how to fix it for sh. For bash I think you would just change it to:
```

if [ $(id -u) != "0" ]; then
    echo "You must run this script as root" >&2
    exit 1
fi

```

It's not really a big deal though since all that is checking is that you are running as root. 

The other thing that I saw is that it copies files to /usr/lib/php5/20060613+lfs:
```

cp ./packages/php_gtk2.so /usr/lib/php5/20060613+lfs
...
cp ./packages/zip.so /usr/lib/php5/20060613+lfs

```

On my system, I have no 20060613+lfs sub-directory under /usr/lib/php5/. I only have 20060613. Try running this:
```

ls -l /usr/lib/php5/

```

If your output looks like:
```

$ ls -l /usr/lib/php5
total 4
drwxr-xr-x 2 root root  33 2008-08-05 15:43 20060613
drwxr-xr-x 2 root root   6 2008-07-23 00:51 libexec
-rwxr-xr-x 1 root root 278 2008-07-23 00:51 maxlifetime

```

then run the commands:
```

cp ./packages/php_gtk2.so /usr/lib/php5/20060613
cp ./packages/zip.so /usr/lib/php5/20060613

```

Note the directory change at the end.

Another thing I noticed is that you are getting:
```

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php/extensions/gd.so' - /usr/lib/php/extensions/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0

```

This could be because the php5-gd package installs gd.so in to /usr/lib/php5/20060613/ (per [link]("http://packages.ubuntu.com/hardy/amd64/php5-gd/filelist")). 
The 60_php-gtk2.ini that the install script copies from the packages directory to /etc/php5/cli/conf.d references a different path:
```

extension_dir = "/usr/lib/php/extensions"

```

Try editing /etc/php5/cli/conf.d/60_php-gtk2.ini using an editor of your choice and edit the path to have /usr/lib/php5/20060613/.

---

### Post by ikxgamex on 2008-08-08
Alright, thanks alot for your help. I did everything you said and have gotten rid of those previous errors. But now when I try to run "php -f src/installer.phpw" from the terminal i get an output that looks like this:

```
PHP Warning:  Module 'zip' already loaded in Unknown on line 0
bcompiler v0.14s	&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Iconfig/constants.phpIconfig/main.phpcHSA_DESK_DIR_ROOT<(src/includes/installer.inc.phpIPs<	<d	php_uname		xLinux	#	cat /etc/lsb-release<
<&#65533;
shell_exec

&&#65533;&#65533;

  /(\r|\n)/si
             <
                <
                   <&#65533;
preg_split

  &&#65533;&#65533;
&#65533;&#65533;B_ID=/si=rch_Preg
  DISTRIB_ID=
             <&#65533;&#65533;&#65533;&#65533;<QQ<<,
                                                       str_replace
                                                                  &@,TUbuntuT &h|&&#65533;|s<<&#65533;	php_uname	&#65533;&#65533;
Windows NT
&#65533;)&&#65533;&#65533;&&#65533;&#65533;m	GtkWizard	D.=0&DpX	set_title	2Halo Stats Archiver: Desktop Edition Configuration2==lp&#65533;set_size_request&#65533;=&#65533;==&#65533;p&#65533;set_icon_from_file c&#65533;HSA_DESK_DIR_ROOT&#65533;&#65533;resource$DardPageng &#65533;= =&#65533; m&#65533;&#65533;

```

All those crazy symbols i have a feeling do not belong there. Is is the "PHP Warning:  Module 'zip' already loaded in Unknown on line 0" error that is causing this?

---

