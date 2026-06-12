---
title: "Installing java JRE 1.3.1_09 on Ubuntu 8.04"
date: 2008-08-16
forum: General Help
---

### Post by abcuser on 2008-08-16
Hi,
I have to install JRE 1.3.1_09 to properly run an old company's Java applet. I have tied running this applet in 1.4, 1.5 and 1.6 but applet doesn't work correctly. So I **_MUST_ install exactly JRE 1.3.1_09** on Ubuntu 8.04.

By the way: I have already installed it on Windows XP SP3 and it works fine - now I would like to have this applet working in Ubuntu.

So far I did the following:
1. I downloaded software from Java Archive page: [http://java.sun.com/products/archive/j2se/1.3.1_09/index.html](http://java.sun.com/products/archive/j2se/1.3.1_09/index.html)

-  I clicked at "Windows (U.S. English / all languages) Solaris SPARC / Solaris x86 Linux" JRE Download link.
-  selected Linux from platform combo-box, checked check box and Continue button
-  I downloaded Linux self-extracting file j2re-1_3_1_09-linux-i586.bin

2) According to install documentation: [http://java.sun.com/products/archive/j2se/1.3.1_09/jre/install-linux.html](http://java.sun.com/products/archive/j2se/1.3.1_09/jre/install-linux.html) I did the following:
$ sudo mkdir /usr/java
$ sudo cp ~/j2re-1_3_1_09-linux-i586.bin /usr/java/j2re-1_3_1_09-linux-i586.bin
$ sudo cd /usr/java
$ sudo ./j2re-1_3_1_09-linux-i586.bin

3. Previous command start installing Java. Install asks for license agreement. I typed yes and press <Enter>

Then I got error:
```
Unpacking...
tail: cannot open `+295' for reading: No such file or directory
Checksumming...
1
The download file appears to be corrupted.  Please refer
to the Troubleshooting section of the Installation
Instructions on the download page for more information.
Please do not attempt to install this archive file.
```
It suggest that download is corrupted but I have downloaded twice and get the same error. And error "tail: cannot open..." error appears before "Checksumming" so it looks it is not a checksumming error. The file install.sfx.8098 was extracted after execution of program.

I am stuck. What to do to install JRE 1.3.1_09?
Thanks,
Abcuser

---

### Post by The Cog on 2008-08-16
I would be inclined to do it from a root shell instead of using sudo because sometimes redirection and creating subprocesses doesn't seem to go right with sudo:
> $ sudo -i
# mkdir /usr/java~/j2re-1_3_1_09-linux-i586.bin /usr/java/j2re-1_3_1_09-# linux-i586.bin
# cd /usr/java
# sh ./j2re-1_3_1_09-linux-i586.bin

But I am inclined to believe it when it says the file is corrupted. Maybe try downloading it with a different downloader? I have lots of success with wget that comes with Ubuntu:
> wget [http://java.sun.com/etc](http://java.sun.com/etc)...

---

### Post by abcuser on 2008-08-16
Hi,
I have used wget as you suggested. So I did:

```

$ sudo -i
# cd /usr/java
# wget http://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/VerifyItem-Start/j2re-1_3_1_09-linux-i586.bin?BundledLineItemUUID=v2NIBe.opLAAAAEbLCsIScxP&OrderID=p6VIBe.o8QMAAAEbGisIScxP&ProductID=b_LACUFBd1AAAAEYfjM5AXiw&FileName=/j2re-1_3_1_09-linux-i586.bin
# sh ./j2re-1_3_1_09-linux-i586.bin
```

Downloaded file is is exactly the same size as previous downloaded file and that is exactly 15415666 bytes.

The error after executing above command is exactly the same.

It looks like binary file executes some command that Ubuntu does not recognized. I have tryied the following.
```
tail +295
```
Is it posible this command runs on other Linux distro and not on Ubuntu?

Any idea how to solve install problem?
Thanks,
Abcuser

---

### Post by txcrackers on 2008-08-16
The *tail* command has changed since this installable archive was created. You should be able to pull the entire thing into an editor and edit the appropriate lines to modify the tail commands within the shell script that's at the "top" of the archive - do [b]not[b/] edit anything below the "cut line" (where the shell script ends and the actual archive starts). Or you can figure out what the installer script is doing and extract the archive manually.

You may end up with some library problems as 1.3 relies on some very old system libraries that don't exist in the current repositories. Be prepared to do some hunting...

---

### Post by Ghadi Rayess on 2008-08-20
Hello,

I have the same problem while installing JRE 1.3.1_1. and i got the same error "tail +227"...

I've extracted the shell script at the top of the archive as txcrackers has mentioned (see code below), but i don't know how to fix the tail command. I'm new to the linux and scripting environment...

Appreciate any help.
Thanx

```
agreed=
while [ x$agreed = x ]; do
    echo
    echo "Do you agree to the above license terms? [yes or no] "
    read reply leftover
    case $reply in
	y* | Y*)
	    agreed=1;;
	n* | n*)
    echo "If you don't agree to the license you can't install this sofware";
    exit 1;;
    esac
done
outname=install.sfx.$$
echo "Unpacking..."
tail +227 $0 > $outname
if [ -x /usr/bin/sum ] ; then
    echo "Checksumming..."

    sum=`/usr/bin/sum $outname`
    index=1
    for s in $sum
    do
	case $index in
	1)  sum1=$s;
	    index=2;
	    ;;
	2)  sum2=$s;
	    index=3;
	    ;;
	esac
    done
    if expr $sum1 != 45742 || expr $sum2 != 14010  ; then
	echo "The download file appears to be corrupted.  Please refer"
	echo "to the Troubleshooting section of the Installation"
	echo "Instructions on the download page for more information."
	echo "Please do not attempt to install this archive file."
	exit 1
    fi
else
    echo "Can't find /usr/bin/sum to do checksum.  Continuing anyway."
fi
chmod +x $outname
echo "Extracting..."
./$outname
echo "Done."
rm -f $outname
exit 0
```

---

### Post by Ghadi Rayess on 2008-08-20
Ok got it. Just have to insert -n after the tail command:

```
...
done
outname=install.sfx.$$
echo "Unpacking..."
[COLOR="Red"]**tail -n +227 $0 > $outname**[/COLOR]
if [ -x /usr/bin/sum ] ; then
    echo "Checksumming..."

    sum=`/usr/bin/sum $outname`
    index=1
...
```

also the checksum should be neglected cause it gives diff values...

---

### Post by Ghadi Rayess on 2008-08-21
I managed to extract the JRE binary... but i'm having the following error whenever i issue the command: "java -version"


```
Segmentation fault
```

Any ideas?!

---

### Post by abcuser on 2008-08-21
Ghadi Rayess,
thanks for help. I have changed bellow code (tail command and add comments before if command checking checksum.
```

tail -n +295 $0 > $outname
#if [ -x /usr/bin/sum ] ; then
#    echo "Checksumming..."
#
#    sum=`/usr/bin/sum $outname`
#    index=1
#    for s in $sum
#    do
#       case $index in
#       1)  sum1=$s;
#           index=2;
#           ;;
#       2)  sum2=$s;
#           index=3;
#           ;;
#       esac
#    done
#    if expr $sum1 != 28071 || expr $sum2 != 15042  ; then
#       echo "The download file appears to be corrupted.  Please refer"
#       echo "to the Troubleshooting section of the Installation"
#       echo "Instructions on the download page for more information."
#       echo "Please do not attempt to install this archive file."
#       exit 1
#    fi
#else
#    echo "Can't find /usr/bin/sum to do checksum.  Continuing anyway."
#fi

```

JRE 1.3.1_09 installed without any error. Which is ok.

But when opening Firefox 3.0.1 browser and fire out URL from address bar that requires 1.3.1_09 JRE Firefox returns message:
"Additional plugins are required to display all the media on this page. Click here to download plugin."
and on clicking it offers plugins:
- GCJ Web Browser Plugin
- The Java Plug-in, Java SE 6,
- The Java Plug-in, Java SE 5.0,
- The GCJ Web Browser Plugin (using OpenJdk).

So browser doesn't recognizes just installed 1.3.1_09 JRE. How to make browser recognize plug-in?
Thanks,
Abcuser

---

### Post by abcuser on 2008-08-21
Hi,
```

cd /usr/java/jre1.3.1_09/bin
./java -version

```
outputs the following error:
/usr/java/jre1.3.1_09/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

According to following Ubuntu threat [http://ubuntuforums.org/showpost.php?p=3365971&postcount=6](http://ubuntuforums.org/showpost.php?p=3365971&postcount=6) it looks some kind of library is missing. Because Ubuntu does not have such a library in repository a RPM file is required and then with alian command to convert to Ubuntu like file.

But RPM file compat-libstdc++-296-2.96-138.i386.rpm is not available any more at location specified [ftp://fr2.rpmfind.net/linux/fedora/core/6/i386/os/Fedora/RPMS/compat-libstdc++-296-2.96-138.i386.rpm](ftp://fr2.rpmfind.net/linux/fedora/core/6/i386/os/Fedora/RPMS/compat-libstdc++-296-2.96-138.i386.rpm). Where to get this library file?
Regards,
Abcuser

---

### Post by abcuser on 2008-08-21
Hi,
I found RPM in [http://rpm.pbone.net/index.php3/stat/4/idpl/3417427/com/compat-libstdc++-296-2.96-138.i386.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/3417427/com/compat-libstdc++-296-2.96-138.i386.rpm.html) scroll down to Download and download file right of ftp.univie.ac.at

I followed the info at [http://ubuntuforums.org/showpost.php?p=3365971&postcount=6](http://ubuntuforums.org/showpost.php?p=3365971&postcount=6) but I still get error:

/usr/java/jre1.3.1_09/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

I just don't know in which dir is libstdc++-libc6.1-1.so.2 expected? Is there any system directory where this file should exist or is there PATH variable that needs to be changed?
Regards,
Abcuser

---

### Post by feistybird on 2008-11-13
Try this:

```
_POSIX2_VERSION=199209 sh j2re-1_3_1_09-linux-i586.bin
```

---

### Post by abcuser on 2008-11-14
Hi,
I have moved to Ubuntu 8.10 and downloaded java binary file as posted in my first post in this thread.

Then I have executed command feistybird posted in this thread:
_POSIX2_VERSION=199209 sh j2re-1_3_1_09-linux-i586.bin

JRE installed successfully. So far so good, but when starting Firefox 3.0.3 and a web page that should fired out this jre 1.3.1_09 and it chooses jre 1.6.

How can I set that Firefox will use jre 1.3 instead of 1.6?
Regards

---

### Post by nenopera on 2010-04-08
inside the bin file is a head with a script and the executable.

Easily you can delete all the lines of the script, make it executable and execute it (that's my case), or you can modify the script:
- add -n after tail 
- change if expr $sum1 != nnnn  || ... to [ $sum1 -ne nnn -o ... ]

but the checksum will not match (I don't know why, in fact). You can also comment the code to verify checksum, but I came out clearing the script lines, and everything works perfect.

---

