---
title: "Web Link URLs are not Recognized"
date: 2008-07-25
forum: General Help
---

### Post by sandman3838 on 2008-07-25
Hello
The bookmarks in Foxfire are just fine and if I place a Web Link/URL on my desktop they are fine also!

However if I place a Web Link/URL in a folder, it's not recognized?  :confused:

What am I missing here?


Thank you.

---

### Post by ad_267 on 2008-07-25
How are you making a link? If I drag a link or a bookmark from firefox into a folder it makes a web link that works.

---

### Post by sandman3838 on 2008-07-25
After thinking about it, some may be leftovers from when I moved files from Winxp to Ubuntu!

Is is possible to change the file extension or file association for the file.  I hate loosing the things!

Thanks for you help.

---

### Post by ad_267 on 2008-07-25
I'm not sure how the web links in windows work. If I open up one made in Ubuntu with a text editor it looks like this:

```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Link to Ubuntu Forums
Type=Link
URL=http://ubuntuforums.org/index.php
Icon=gnome-fs-bookmark
```

If the links from windows are just plain text files then you could possibly modify them to fit this format.

---

### Post by sandman3838 on 2008-07-27
I think I might have to give up in this one?
Oh if your interested the Winxp/Firefox links in question here all have a .URL extension.

If that helps?

Thanks you!  :)

---

### Post by ad_267 on 2008-07-28
I found this link that explains how a url file works: [http://www.cyanwerks.com/file-format-url.html](http://www.cyanwerks.com/file-format-url.html)

So if you wanted it wouldn't be too difficult to write a bash or python script that converted a bunch of .url files into the .desktop files used in Ubuntu.

---

### Post by ad_267 on 2008-07-28
I needed some python practice so I wrote this. It will convert a .url file to a .desktop one.

```

#! /usr/bin/env python

import sys
import os
import re

def convert_url_file(infile, outfile):
    """
    Convert an input file in the .url file format used by
    windows into the .desktop format used by GNOME
    """
    
    # find the line with url= at the beginning, this is
    # the only line we care about
    for line in infile:
        if re.search('^url\=',line.lower()):
            url = line
    
    # get the url
    try: url = url[4:].strip()
    except:
        print "Error: url not found in file."
        exit(1)
    
    # write text to output file in GNOME .desktop format
    outfile.write("[Desktop Entry]\n"+\
        "Version=1.0\n"+\
        "Encoding=UTF-8\n"+\
        "Name="+outfile.name.replace('.desktop','')+"\n"+\
        "Type=Link\n"+\
        "URL="+url+"\n"+\
        "Icon=gnome-fs-bookmark\n")
    

if __name__ == "__main__":
    if len(sys.argv) < 2:
        print "Usage: "+sys.argv[0]+" url_file.url"
        exit(1)
    try:
        infile = open(sys.argv[1],"r")
    except:
        print "Error: Input file "+sys.argv[1]+" could not be opened."
        exit(1)    
    
    try:
        outfile = open(os.path.splitext(os.path.split(infile.name)[1])[0]+".desktop", "w")
    except:
        print "Error: Output file "+os.path.splitext(os.path.split(infile.name)[1])[0]+".desktop could not be opened."
        exit(1)
    
    convert_url_file(infile, outfile)
    
    infile.close()
    outfile.close()
    
        

```

Copy that into a file and save it as url2desktop.py then make the file executable.

If you put that in the same directory as the .url files you can use 
```
find . -name "*.url" -exec ./url2desktop.py {} \;
```
to make a .desktop file for all the .url files in a directory or you can put it in ~/bin so that you can run it from any directory and don't have to use the "./" part.

---

### Post by sandman3838 on 2008-07-28
Got it!
Before I read the last two replies above I found this last night- [http://ubuntuforums.org/showthread.php?t=495131&page=5]("http://ubuntuforums.org/showthread.php?t=495131&page=5")

It fine and now the URL open up to Firefox!

There is one small issue however:
If I read it correctly Globally all the URL icons should have changed to what I selected?  They didn't!  What I selected was in a scalable folder in my /home/.icons folder.

Any ideas?

Oh!  Thank you one and all for your help!
You have all been great!

---

### Post by ad_267 on 2008-07-28
Ok if you followed those steps I'm not sure why the icon isn't changing. It looks like someone else was having that same problem.

> one little question. I use hardy heron and don't get the icon to show up. Can you confirm this in hardy?
funny thing that the search result in tracker does show the icon I supplied in assogiate (see attached screenshot). Very, very strange...

This was the reply:
> I'm not sure that I will be able to help you because, as I previously pointed out in my instruction guide, I am not experienced with Ubuntu (or Linux in general). Also, I haven't used Linux for quite a while, so the last version of Ubuntu I used was 7.10. I therefore can't say whether what you're seeing is an 8.04 specific issue or not.

However, the fact that you get the correct icon in Tracker suggests that Assogiate has done it's job properly and that it's just Nautilus playing up with regards to icon display. So you could try updating the system icon cache to see if that fixes the problem (I can't guarantee that this will help though).


Run the following command in the terminal window and then restart X (or just reboot your machine if you prefer) and see if it makes a difference

---

### Post by sandman3838 on 2008-07-30
Hello 

ad_267

I'm back.
I read what you wrote and snd since you were so nice to write that code for be I have to give it a try!
It would seem that I'm still having that issue.
I think that prevous "fix" was just for the one file not all!
What I get when I open this .URL that I just moved to my Desktop is Firefox, in a blank page showing:

[InternetShortcut]
URL=http://www.bodybuilding.com/fun/index.html

Thats it?

You know if it helps at all the all the files in question are folders in the /home/kevin

Sorry for being a pain but being an X Dos/Windows user I'm use to just Highlighting a UNKNOWN file type, selecting "Open With" and re associating it with a supported program?  Then "ALL" the files with *.??? would open with that program.  This seems a little to difficult when it shouldn't be, not for an OS with this type of potential?

Anyway....

I made the file as you suggested with all that code:
url2desktop.py

Next I placed the file in the /bin

TERMINAL:
sudo cp ~/Desktop/*.py /bin

However when run the file 

TERMINAL:
find . -name "*.url" -exec ./url2desktop.py {} \;
or
find . -name "*.url" -exec
(you mentioned - so that you can run it from any directory and don't have to use the "./" part.)

I get - 
find: missing argument to `-exec'

Did I do something wrong?

---

### Post by ad_267 on 2008-07-31
If you have it in /bin then you should be able to use this:

```
find /home/kevin -name "*.url" -exec url2desktop.py {} \;
```

This will keep the old .url files intact but make new .desktop files that should work well, so you can delete the .url files if you don't need them any more.

the ./ part I said before just means look in the current directory for the script to run.

I guess you can't just change the "open with" because the .url files were handled by Windows and Windows uses the url file to open your browser. Firefox itself in Windows cannot open a .url file.

---

### Post by sandman3838 on 2008-07-31
Thanks for the help!
This time it did run.  It now looks ad if its trying to run an change all the URL in my Home and sub folders.  I mean the first time there was that EXE issue however this time it scrolled quit a bit just listing over and over:

find: url2desktop.py: Permission denied

I did do a backup of the file you made.
Next I checked a URL file Permissions tab through Properties and it was set to.
x Dead and Write (all)
x Allow executing file as a program

The url2desktop.py
I tried several access options in the permissions Tab and the result was always Permision denied!

Hey I know you busy but if this is getting to weird and you wish it would just go away, that's fine I'll just live with the files the way they are. If not and this is become like an itch you can't quite scratch then, what next?

Thanks for your help!  :)

---

### Post by sandman3838 on 2008-07-31
I'm back!

As far as loading URLs they are working.
In the properties for the URLs there is a choice to open it with FIREFOX or WEB BROWSER.  The Web Browser works and it opens to Firefox anyway.

As for the Icons I did a search and Listed them all and I'm going to change it manually!

Again thank you so very much for your help! :)

---

### Post by ad_267 on 2008-08-01
I'm not sure why it would be saying that sorry. I've tried the same thing and it's working here.

Does it work if you just run the program with a url file, like "url2desktop.py ~/website.url"?

Another way to do this would be like:
```

cd
IFSBAK=$IFS
IFS=$'\n'
for file in `ls *.url`
do
url2desktop.py "$file"
done
IFS=$IFSBAK

```

Also note that this is case sensitive so if there are some files that have a ".URL" extension instead of ".url" you will have to run it again and change that line to "for file in `ls *.URL`"

And these '`' are backticks, not single quotes.

---

### Post by sandman3838 on 2008-08-01
Hi Again!
Your very persistent!  :)

I should note that even thought they all have the same default Icon that a few of the URL/url files do open to Foxfire.  Why I have know idea the Properties on the files look the same.  Perhaps it was from some of what you wrote here and it worked?

Still when I open a troubled URL/url file I get:

"Firefox doesn't know how to open this address, because the protocol (basehttp) isn't associated with any program."

Now I hope to answer some of your questions?
With url2desktop.py in my /bin folder (also I have a copy on my desktop):

TERMINAL:
find /home/kevin -name "*.url" -exec url2desktop.py {} \;

Terminal scrolled down with....

RESULT:
find: url2desktop.py: Permission denied
find: url2desktop.py: Permission denied
kevin@Larry-Ubuntu:~$ 

Next I tried uppercase:

TERMINAL:
find /home/kevin -name "*.URL" -exec url2desktop.py {} \;

Terminal scrolled down again but not as long as the first run.
Fewer files I guess?

RESULT:
find: url2desktop.py: Permission denied
find: url2desktop.py: Permission denied
kevin@Larry-Ubuntu:~$ 

Next I ran the text just straight and with "sudo" like you mentioned:

TERMINAL:
cd
IFSBAK=$IFS
IFS=$'\n'
for file in `ls *.url`
do
url2desktop.py "$file"
done
IFS=$IFSBAK

RESULT:
kevin@Larry-Ubuntu:~$ cd
kevin@Larry-Ubuntu:~$ IFSBAK=$IFS
kevin@Larry-Ubuntu:~$ IFS=$'\n'
kevin@Larry-Ubuntu:~$ for file in `ls *.url`
> do
> url2desktop.py "$file"
> done
ls: cannot access *.url: No such file or directory
kevin@Larry-Ubuntu:~$ IFS=$IFSBAK
kevin@Larry-Ubuntu:~$ 

Now one last thing I should mention.  I put this all to the Firefox forum to see what might turn up.  Please check this link out, it's over my head perhaps you can understand it?

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/676741.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/676741.html)

Thanks again!  Have a good weekend!

---

### Post by ad_267 on 2008-08-01
I've modfied that python script in my post above so it will hopefully get rid of that problem but I'm not really sure.
Can you open that file that firefox says it can't open with a text editor and show me what it says? Also the .url file that it came from.

Ok so is /home/kevin where the .url files are not your home directory? The "cd" line just changes directory into your home directory. You might want to do something like make a new directory for the links just to make it easier to sort out what's going on. This will make a new directory called newlinks in your home directory and output the links to there:
```

mkdir ~/newlinks
cd ~/newlinks
IFSBAK=$IFS
IFS=$'\n'
for file in `ls /home/kevin/*.url`
do
url2desktop.py "$file"
done
IFS=$IFSBAK

```

Where /home/kevin/ should be where all the .url files are currently.

Just to explain a bit more, that program url2desktop.py takes one input which is the name of a .url file, eg "url2desktop.py link.url" and then creates a .desktop file in the current directory which should be able to be opened by firefox and it leaves the .url file as it was.

Hopefully this sort of makes sense.

---

### Post by sandman3838 on 2008-08-01
You know the weird thing is, that some of them work?
I have been looking around and many do indeed work now!
If you see an issue from all this or perhaps something that I have been doing wrong then great.
If not, I'm thinking about letting go and deleting them as I find them.
You have put to much work into this my friend.

It's your call!

Running that last script returned the following info:

kevin@Larry-Ubuntu:~/newlinks$ cd ~/newlinks
kevin@Larry-Ubuntu:~/newlinks$ IFSBAK=$IFS
kevin@Larry-Ubuntu:~/newlinks$ IFS=$'\n'
kevin@Larry-Ubuntu:~/newlinks$ for file in `ls /home/kevin/*.url`
> do
> url2desktop.py "$file"
> done
ls: cannot access /home/kevin/*.url: No such file or directory
kevin@Larry-Ubuntu:~/newlinks$ IFS=$IFSBAK


Now, here is the information of one file that Passed and the other failed.  Both were in the same folder!

********** 

This one FAILED same folder:
File name: Welcome to Office of Technology Management Site!.url
Link:   [http://www.y12.doe.gov/techmgt/who/welcome.htm](http://www.y12.doe.gov/techmgt/who/welcome.htm)

Text:
[DEFAULT]

BASEURL=http://www.y12.doe.gov/techmgt/who/welcome.htm

[InternetShortcut]

URL=http://www.y12.doe.gov/techmgt/who/welcome.htm

Modified=7057AD1A2572C301E9


**********

This one PASSED same folder:
File name: Buy Cheap Discount Software Sale Office 2007 Professional Academic 269-11095.url
Link:[http://www.viosoftware.com/Office+2007+Google/Office+2007+Professional+Academic.html](http://www.viosoftware.com/Office+2007+Google/Office+2007+Professional+Academic.html)

Text:
[InternetShortcut]

URL=http://www.viosoftware.com/Office+2007+Google/Office+2007+Professional+Academic.html?osCsid=bb6eb4bdbdc9cea8738f2e2e1488a248

IDList=

IconFile=http://www.viosoftware.com/images/favicon.ico

IconIndex=1

[{000214A0-0000-0000-C000-000000000046}]

Prop3=19,2

[DEFAULT]

BASEURL=http://www.viosoftware.com/Office+2007+Google/Office+2007+Professional+Academic.html?osCsid=bb6eb4bdbdc9cea8738f2e2e1488a248

**********

Thanks for your help!
If you need more info please let me know!

---

### Post by ad_267 on 2008-08-01
Haha I find it hard to let go of a problem to solve!

I modified my post with the script so that it should work I think for those other links.

Are the links actually in /home/kevin or are they in subdirectories of that?
If they're in different subdirectories then you can use what I posted before but just change the "/home/kevin/*.url" part.

If they are 1 subdirectory deep you can use "/home/kevin/*/*.url", for 2 use "/home/kevin/*/*/*.url" etc.

The method using find would look through all subdirectories but that wasn't working obviously.

---

### Post by sandman3838 on 2008-08-01
Hello I'm back!

Like a bad dream it's still acting up on certain url files.:confused:
Here are the results...

Oh!  An to answer your question the url's they are indeed scattered in sub_folders within kevin/home/my documents/*

I ran script this line by line and again all at once letting it run all at once.

I wanted to get them all so I expanded the search!

TERMINAL:
mkdir ~/newlinks
cd ~/newlinks
IFSBAK=$IFS
IFS=$'\n'
for file in `ls /home/kevin/*/*/*/*/*.url`
do
url2desktop.py "$file"
done
IFS=$IFSBAK

RESULT:

kevin@Larry-Ubuntu:~/newlinks$ IFS=$IFSBAK
kevin@Larry-Ubuntu:~/newlinks$ cd ..
kevin@Larry-Ubuntu:~$ mkdir ~/newlinks
mkdir: cannot create directory `/home/kevin/newlinks': File exists
kevin@Larry-Ubuntu:~$ cd ~/newlinks
kevin@Larry-Ubuntu:~/newlinks$ IFSBAK=$IFS
kevin@Larry-Ubuntu:~/newlinks$ IFS=$'\n'
kevin@Larry-Ubuntu:~/newlinks$ for file in `ls /home/kevin/*/*/*/*/*.url`
> do
> url2desktop.py "$file"
> done
bash: /usr/local/bin/url2desktop.py: Permission denied
bash: /usr/local/bin/url2desktop.py: Permission denied
etc..... 
bash: /usr/local/bin/url2desktop.py: Permission denied
kevin@Larry-Ubuntu:~/newlinks$ IFS=$IFSBAK
kevin@Larry-Ubuntu:~/newlinks$ 

What now!

It's late here I'm headed for bed I'll try whatever you suggest tomorrow!  Good night!  :)

Again thanks for all you help.

---

### Post by ad_267 on 2008-08-02
Damn so close!

I think it must be a problem with the permissions on that file. Can you post the output of.
```
ls -l /usr/local/bin/url2desktop.py
```

---

### Post by sandman3838 on 2008-08-02
Ill do as you requested ASAP and paste it in in just a moment!

But first I moved one Passed and One Failed file to my desktop and I have some details on both!

**** DEFINITION TWO URLS ONE FAILS & ONE THAT PASSES  **** 

FAILS:
FILE NAME: Dell Careers.url
        PROPERTIES BASIC TAB:
                Type - Microsoft Internet Shortcut
                Size - 176 bytes
                Location - /home/kevin/Desktop
                Volume - unknown
                Mime type - text/x-url

        PROPERTIES EMBLEMS TAB: (usual selection)
                
        PROPERTIES PERMISSIONS TAB:
                Owner - kevin
                Access - read and write
                Group - kevin
                Access - read and write
                Others Access - Read and Write
                Execute - X Allow executing file as program
                Selinux content - Unknown

        PROPERTIES OPEN WITH TAB:
                O - Firefox Web Browser
                O - Text Editor
                X - Web Browser

        PROPERTIES NOTES TAB: (empty)
        
TEXT:
[DEFAULT]
BASEURL=http://dellapp.us.dell.com/careers/app/default.asp
[InternetShortcut]
URL=http://dellapp.us.dell.com/careers/app/default.asp
Modified=1078A3262CE3C40125


PASSES:
FILE NAME: BODYBUILDING MAIN PAGE.url
        PROPERTIES BASIC TAB:
                Type - Microsoft Internet Shortcut
                Size - 68 bytes
                Location - /home/kevin/Desktop
                Volume - unknown
                Mime type - text/x-url

        PROPERTIES EMBLEMS TAB: (usual selection)
                
        PROPERTIES PERMISSIONS TAB:
                Owner - kevin
                Access - read and write
                Group - kevin
                Access - read and write
                Others Access - Read and Write
                Execute - X Allow executing file as program
                Selinux content - Unknown

        PROPERTIES OPEN WITH TAB:
                O - Firefox Web Browser
                O - Text Editor
                X - Web Browser

        PROPERTIES NOTES TAB: (empty)
        
TEXT:
[InternetShortcut]
URL=http://www.bodybuilding.com/fun/index.html

Note - I went through a bunch that WORKED and some that failed.  
The ones that worked showed text like:

TEXT:
[InternetShortcut]
URL=http://www.bodybuilding.com/fun/index.html

Now the ones that FAILED looked like:
TEXT:
[DEFAULT]
BASEURL=http://dellapp.us.dell.com/careers/app/default.asp
[InternetShortcut]
URL=http://dellapp.us.dell.com/careers/app/default.asp
Modified=1078A3262CE3C40125

I wonder if that could be the culprit here what ever that extra text (BASEURL) is?  Ubuntu and Firefox don't like it?  What did Bill Gates and Microsoft do there?:confused:

---

### Post by sandman3838 on 2008-08-02
Here is the info you asked for:

kevin@Larry-Ubuntu:~$ ls -l /usr/local/bin/url2desktop.py
-rw-r--r-- 1 root root 1443 2008-07-29 23:06 /usr/local/bin/url2desktop.py
kevin@Larry-Ubuntu:~$

---

### Post by ad_267 on 2008-08-02
Ok it's not showing as executable so enter this in a terminal:
```
sudo chmod a+x /usr/local/bin/url2desktop.py
```

Then if you run the ls -l command again it should look like:
```
-rwxr-xr-x 1 root root 1443 2008-07-29 23:06 /usr/local/bin/url2desktop.py
```

Also did you remove the file that was in /bin? Run "which url2desktop.py" to make sure that it says "/usr/local/bin/url2desktop.py"

---

### Post by sandman3838 on 2008-08-03
Per you request here is the info you asked!

Also before running the steps you asked for, I did remove the file that was in /bin? and checked that "url2desktop.py" was in the "/usr/local/bin/".  The only two remaining is the one on my desktop the the other one in /usr/local/bin.

YOUR QUESTION:
Ok it's not showing as executable so enter this in a terminal:

Code:
sudo chmod a+x /usr/local/bin/url2desktop.py

Then if you run the ls -l command again it should look like:
Code:
-rwxr-xr-x 1 root root 1443 2008-07-29 23:06 /usr/local/bin/url2desktop.py

RESULT:
OK!  In the /usr/local/bin/  there is just the one file url2desktop.py!
I did a properties on it and Permissions does show it as [x] Allow executing file as program.

FIRST - sudo chmod a+x /usr/local/bin/url2desktop.py
Returned with :

kevin@Larry-Ubuntu:~$ sudo chmod a+x /usr/local/bin/url2desktop.py
kevin@Larry-Ubuntu:~$ 

SECOND - ls -l
Returned with:
kevin@Larry-Ubuntu:~$ ls -l
total 64
drwxr-xr-x  3 kevin kevin 4096 2008-08-02 19:13 1A_UBUNTU
drwxr-xr-x  7 kevin kevin 4096 2008-08-02 21:58 btnx-0.4.9
drwxr-xr-x 11 kevin kevin 4096 2008-08-02 21:59 btnx-config-0.4.8
-rw-r--r--  1 kevin kevin  413 2008-08-03 11:12 Current project
-rw-r--r--  1 kevin kevin  413 2008-08-03 11:12 Current project~
drwxr-xr-x  3 kevin kevin 4096 2008-08-03 11:27 Desktop
drwxr-xr-x 20 kevin kevin 4096 2008-08-02 12:13 Documents
drwxr-xr-x  4 kevin kevin 4096 2008-07-30 00:42 Downloads
drwxr-xr-x  2 kevin kevin 4096 2008-07-30 23:58 dwhelper
lrwxrwxrwx  1 kevin kevin   26 2008-07-23 21:54 Examples -> /usr/share/example-content
drwxr-xr-x  8 kevin kevin 4096 2008-07-24 21:00 Music
-rw-r--r--  1 kevin kevin 1240 2008-07-25 19:02 MY CODE NOTES~
drwxr-xr-x  2 kevin kevin 4096 2008-08-01 20:38 newlinks
drwxr-xr-x 24 kevin kevin 4096 2008-07-27 16:07 Pictures
drwxr-xr-x  2 kevin kevin 4096 2008-07-26 19:13 System Infomation tool
drwxr-xr-x  7 kevin kevin 4096 2008-07-30 19:06 Theme Packages
drwxr-xr-x  3 kevin kevin 4096 2008-08-01 00:53 Videos
kevin@Larry-Ubuntu:~$ 

Does this help????
Thanks again.

---

### Post by ad_267 on 2008-08-04
By ls -l I meant the whole "ls -l /usr/local/bin/url2desktop.py" but that should have worked fine.

So now if you do:
```

cd ~/newlinks
find /home/kevin -name "*.url" -exec url2desktop.py {} \;

```

it should make the new links in ~/newlinks

---

### Post by sandman3838 on 2008-08-04
Hello I'm back!
Sorry for not getting back sooner but things have been busy here.
Yard work in 90 degrees of weather sucks!

I started back the your posting #23 just the other day.

FIRST:
Code:
sudo chmod a+x /usr/local/bin/url2desktop.py
RESULTS:
None - After admin password, just back to prompt.

SECOND:
Code:
ls -l /usr/local/bin/url2desktop.py
RESULTS:
-rwxr-xr-x 1 root root 1443 2008-07-29 23:06 /usr/local/bin/url2desktop.py

THIRD:
Code:
cd ~/newlinks
RESULTS:
kevin@Larry-Ubuntu:~/newlinks$ 

FOURTH:
Code:
find /home/kevin -name "*.url" -exec url2desktop.py {} \;
RESULTS:
kevin@Larry-Ubuntu:~/newlinks$ find /home/kevin -name "*.url" -exec url2desktop.py {} \;
find: /home/kevin/.mozilla/firefox/vkuuxfit.default/chrome/filmstrips: Permission denied

kevin@Larry-Ubuntu:~/newlinks$ sudo find /home/kevin -name "*.url" -exec url2desktop.py {} \;
find: /home/kevin/.gvfs: Permission denied

Does this help?  :confused:

---

### Post by ad_267 on 2008-08-05
You didn't need to do the sudo. That might have caused problems because now all the links will be owned by root. The .gvfs is a special folder and there was an error because it couldn't be searched but that doesn't matter.

Are all the links in the newlinks folder? There should be now.

Those links will probably be owned by root because you ran it as sudo so you can do this to make sure you own them:
```
sudo chown -R your_user_name_here ~/newlinks
sudo chgrp -R your_user_name_here ~/newlinks
```

---

### Post by sandman3838 on 2008-08-05
Hey!  I'm back!

Sorry about running sudo I just took it for granted?  :(

Everything seems fine now and I did run both 

sudo chown -R kevin ~/newlinks
sudo chgrp -R kevin ~/newlinks

Both seemed to have worked.
No errors or anything.

---

### Post by sandman3838 on 2008-08-05
Sorry I went back and read you last letter again.
There is a /home/kevin/newlinks
and it would seem that they are all working?

Thank you so very much!
Your the MAN!  :) :) :)  :popcorn:

You should end this with a ABC how to in case some other nut comes along with the same issue?  :KS

---

### Post by sandman3838 on 2008-08-05
As you recall the URL with the "ISSUE" had a mention of BASEHTTP in the file when I told it to open To Text!  In the 

Firefox doesn't know how to open this address, because the protocol (basehttp) isn't associated with any program

In the 
/home/kevin/newlinks
there are some 278 files that have been corrected.
This also means that there are some 278 bad files in the
/home/kevin/Documents

I would like to get them out of there?

Would you have a good command line to search and delete the bad files? 

Remember what I have added to UBUNTU since I started is in 
/home/kevin/Desktop
/home/kevin/1A_UBUNTU
/home/kevin/newlinks

The dead files are scattered in folders and sub-folders in:
/home/kevin/Documents

Thanks again!  :)

---

### Post by ad_267 on 2008-08-06
You can search for and delete the files using this:

```
find /home/kevin/Documents -name "*.url" -exec rm {} \;
```
```
find /home/kevin/Documents -name "*.URL" -exec rm {} \;
```

That searches for the same files but instead of executing the url2desktop program it executes rm which deletes the file.

---

### Post by sandman3838 on 2008-08-06
Cool thanks that did it!  :popcorn:

Wow!  Finally Done!  :)

---

### Post by ad_267 on 2008-08-06
Haha yup, awesome.

---

### Post by ShinobiTeno on 2008-12-04
Guys, thanks for your work! ):P
My problem is solved too.

Im working on taged urls, that are inherited inside html files with tags and autoredirection. And can be grep'ed for tags. Still I had the unsolved legacy problem with .url crap...

Many Thanks!!! 
:KS:KS:KS:KS:KS

---

