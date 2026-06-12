---
title: "RapidShare Linux Script"
date: 2008-11-07
forum: General Help
---

### Post by Ciwan on 2008-11-07
Hi Guys

I am a heavy RapidShare user and I want to Upload stuff to RapidShare from my Ubuntu System.

The RapidShare team has created a Script for Linux systems, but I don't know how to use it !!

I would be very grateful if someone can tell me how I can upload files using that script.

Here is a link to that script >> [http://rapidshare.com/news1.html](http://rapidshare.com/news1.html)

you might need to scroll down to the 6th subject in order to see the info about the script.

Thank You.

---

### Post by EXCiD3 on 2008-11-07
The script is a perl script, so you will need to run it using Perl. Check this out for the basics: [http://www.tech-geeks.org/contrib/mdrone/LinuxWorkshop/newbie-linux-manual/sections/perl.html](http://www.tech-geeks.org/contrib/mdrone/LinuxWorkshop/newbie-linux-manual/sections/perl.html)
 
Hope that helps get you started! Rapidshare is really neat, i absolutely love using JDownloader with it, everything is streamlined using that. :)

---

### Post by Ciwan on 2008-11-07
Hi EXCiD3

I don't really know what Perl is !! But I will go and read that link you've kindly provided.

Also is JDownloader a Download Manager ??

Cause I have been looking for a Download Manager for Ubuntu for aaages :(

Thank You Sir.

---

### Post by Ciwan on 2008-11-07
I'm sorry to say that Link didn't help me at all :(

I still don't know how to run that Perl Script for Rapidshare :(

Any help **please** !

---

### Post by kbf on 2008-11-07
use modrapi

here is more about

[http://m0ds-ubuntu.blogspot.com/2008/01/en-rapidsharecom-download-manager-for.html](http://m0ds-ubuntu.blogspot.com/2008/01/en-rapidsharecom-download-manager-for.html)

---

### Post by LateNiteTV on 2008-11-07
```
perl perlscript.pl
```

---

### Post by Sam on 2008-11-07
I think perl is installed by default, if not```
sudo apt-get install perl
```

There are some info in the script if you open it with a text editor:

```
To upload a file, put this script on a machine with perl installed and use the following syntax:
perl rsapi.pl free mytestfile.rar        (this uploads mytestfile.rar as a free user)
perl rsapi.pl prem archive.rar 334 test  (this uploads archive.rar to the premium-zone of login 334 with password test)
perl rsapi.pl col a.rar testuser mypw    (this uploads a.rar to the collector's-zone of login testuser with password mypw)

```

---

### Post by EXCiD3 on 2008-11-07
> **Ciwan said:**
> Hi EXCiD3

I don't really know what Perl is !! But I will go and read that link you've kindly provided.

Also is JDownloader a Download Manager ??

Cause I have been looking for a Download Manager for Ubuntu for aaages :(

Thank You Sir.

Hey sorry i didnt explain. You may need to install Perl before you can use the script. like everyone has mentioned, open terminal and run perl <scriptname>.pl and that should work. Also, JDownloader is a java program that you can run as a download manger for almost ALL of the rapidshare type sites. just copy paste the links in, hit start and it downloads them all AND extracts it for you! :D [www.jdownloader.org](www.jdownloader.org)

---

### Post by cusco on 2008-12-04
TO UPLOAD

I use [http://images.rapidshare.com/software/rsapiresume.pl](http://images.rapidshare.com/software/rsapiresume.pl) to upload.
I just download that script and put it on /usr/local/bin/rsapi
I just call it out:

rsapi big-file.zip prem username password

then you can resume uploads!


TO DOWNLOAD

I made the following script:

wget.sh
```
#!/bin/bash
for i in $(grep ^http $1); do

#       curl -A "Mozilla/4.0" -C -L -O --cookie /home/cusco/.cookies/rapidshare $i;

       wget -b -c --header="Cookie: user=4214181-%62%6F%61%63%6C%31%55" $i;


done

```

then I save the link list in lets say: links.txt

then:

sh wget.sh links.txt


ofcourse you have to get the cookie first.

---

### Post by marinche on 2008-12-07
where to put the file I would like to upload

---

### Post by larytet on 2009-01-06
Bash script for download from RS premium accounts. Copy from some other script called AreGet with very minor corrections

```


#    This program is free software: you can redistribute it and/or modify
#   it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#   This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with this program.  If not, see <http://www.gnu.org/licenses/>.

# Important ! Make sure that "Direct download" is enabled in the premium
# account settings

#!/bin/bash

VERSION=.03
LOGINURL=https://ssl.rapidshare.com/cgi-bin/premiumzone.cgi

#modify following two lines to point to the files containing 
#rapidshare account username and login
#each file should contain only one line 
USERNAME=`cat ~/rapid_username`
PASSWORD=`cat ~/rapid_password`

#file where wget will store rapidshare.com cookie
COOKIE_FILE=~/rapid_cookie
RATE=450k


if [[ ! -z $3 ]]; then
    echo "Invalid Arguments"
    exit
fi

if [[ ! -z $2 ]]; then
    FILELIST=$2
else
    FILELIST=$1
fi

NAME=$0

trap "rm $TEMP_FILE; exit" SIGHUP SIGINT SIGTERM

getfile(){
    wget --limit-rate=$RATE --load-cookies $COOKIE_FILE $2 $1 
}

testfile(){

    wget $1 --load-cookies  $COOKIE_FILE --spider -o wget_test.log
    filelen=`grep "Length: [0-9,]* " wget_test.log -o | tr -d "," | grep "[0-9]*" -o`    

    filename=`echo $1 | grep '\/[^\/]*$' -o | tr -d "/"`
    
    echo Current File: $filename

    if [[ -f $filename ]]; then
        current=`du -b $filename | cut -f1 `
        echo $current of $filelen bytes completed
        if [[ $current -lt $filelen ]]; then
            echo $filename incomplete, finishing download...
            getfile $1 -c
        elif [[ $current -gt $filelen ]]; then
            echo local $filename is larger than on server....
            echo something is wrong....
            echo exiting....
            exit
        elif [[ $current -eq $filelen ]]; then
            echo $filename is complete
            # Do nothing, move on to next file
        else
            echo something is b0rken.
            exit
        fi
    else
        echo starting download...
        getfile $1
    fi
    
    rm wget_test.log
}

testfiles(){
    count= cat ${FILELIST} | grep 'http://.*' | wc -l | tr "\n" " " 
    echo $count links found in $FILELIST
    for link in `cat ${FILELIST}`; do
        echo "Getting ${link}"
        testfile $link
    done
}


getcookie(){
    if [[ -e  $COOKIE_FILE ]] && [[ ! -r  $COOKIE_FILE ]]; then
        echo "cookie file  $COOKIE_FILE error"
        exit
    fi
    echo "Getting cookie for username=$USERNAME pass=$PASSWORD from $LOGINURL ..."
    wget --save-cookies $COOKIE_FILE --post-data \
       "login=$USERNAME&password=$PASSWORD" -O - $LOGINURL > /dev/null



    echo "Cookie Saved..."
}

startDown(){
    echo "AreGet ${VERSION} By Underpenguin"
    
    if [[ ! -r  $COOKIE_FILE ]]; then
        echo "no cookie found, getting cookie..."
        getcookie
    fi

    testfiles
}

startDown



```

---

### Post by deliiled on 2009-04-22
its working good.. but i want to download or upload via teleglobe #2 .. can we add new codes to script to choose teleglobe #2 ???
(if there is a teleglobe #2 choice. because some links have no teleglobe #2 choice)

sorry.. i have terrible english :)

---

### Post by crazybuntu on 2009-06-20
is there a GUI for this feature ???

---

### Post by darthrax on 2009-08-19
hello all,

i've written a nautilus script which allows right-click upload to rapidshare. you can check it out at [http://ubuntuforums.org/showthread.php?t=1195389](http://ubuntuforums.org/showthread.php?t=1195389)

---

### Post by sniper11 on 2009-10-09
Here's a rapidshare script for free users:

[http://sniper11powers.blogspot.com/2009/03/rapidshare-automatic-download-script.html](http://sniper11powers.blogspot.com/2009/03/rapidshare-automatic-download-script.html)

It'll download the files contained in a list and will wait for some time if the download limit has been exceeded.(see above link for more details)

Hope it helps anyone out :)

//sniper11

---

### Post by alien-377h on 2009-10-24
> **Sam said:**
> I think perl is installed by default, if not```
sudo apt-get install perl
```

There are some info in the script if you open it with a text editor:

```
To upload a file, put this script on a machine with perl installed and use the following syntax:
perl rsapi.pl free mytestfile.rar        (this uploads mytestfile.rar as a free user)
perl rsapi.pl prem archive.rar 334 test  (this uploads archive.rar to the premium-zone of login 334 with password test)
perl rsapi.pl col a.rar testuser mypw    (this uploads a.rar to the collector's-zone of login testuser with password mypw)

```


Don't if it's working for you. :confused:

But the following codes are working for me  :guitar:

```

perl rsapi.pl mytestfile.rar   (this uploads mytestfile.rar as a free user)
perl rsapi.pl archive.rar prem 334 test  (this uploads archive.rar to the premium-zone of login 334 with password test)
perl rsapi.pl a.rar col testuser mypw    (this uploads a.rar to the collector's-zone of login testuser with password mypw)

```

Source:
```
http://images.rapidshare.com/software/rsapi.pl
```

---

### Post by panaeolus on 2010-01-04
rapidshare uploader from the site
works perfetly with wine
no script needed

---

### Post by djdan2k8 on 2010-02-03
Dont know if this helps im trying it now

This script will compress your selected files as rar (99mb per file, it will split the files, if they are bigger than 99mb.), upload them then delete the rar files after upload.

Incase you do not have rar package installed, this is a good time to install it:

$sudo apt-get install rar

You also need zenity package which is pre-installed with ubuntu:

$sudo apt-get install zenity

Navigate to your ~/.gnome2/nautilus-scripts folder and copy rsapi.pl (You can download this file from rapidshare, or see below) as .rsapi.pl:

$cd ~/.gnome2/nautilus-scripts
$wget -c [https://dl.getdropbox.com/u/612498/rsapi.pl](https://dl.getdropbox.com/u/612498/rsapi.pl) && mv rsapi.pl .rsapi.pl && chmod +x .rsapi.pl

Now download RapidUpload script and save it to ~/.gnome2/nautilus-scripts:

$cd ~/.gnome2/nautilus-scripts
$wget -c [https://dl.getdropbox.com/u/612498/RapidUpload](https://dl.getdropbox.com/u/612498/RapidUpload) && chmod +x RapidUpload

Now edit ~/.gnome2/nautilus-scripts/RapidUpload script and change username and password parts:

$gedit ~/.gnome2/nautilus-scripts/RapidUpload

You are going to change this part with your username password:

rapidshareusername=username 
rapidsharepassword=password

Save it when you are done.


If you do not have a Rapidshare premium account, open RapidUpload and change

accounttype=prem

part with accounttype=col (collector's account), or accounttype=free (free user = anonymous)

PS : It is under rapidsharepassword=password part

You can now Right Click any file(s), and select Scripts > RapidUpload to upload your files.

Tested on Ubuntu Karmic Alpha 4, Ubuntu Jaunty, Crunchbang Linux.

Have fun!

---

