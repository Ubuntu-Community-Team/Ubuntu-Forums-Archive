---
title: "Need FTP help"
date: 2008-10-14
forum: General Help
---

### Post by swbrenton on 2008-10-14
I have tried (and failed) to get downloads using gFTP and FileZilla.
I admit, I am real ignorant in the use of FTP programs.  However, when I used windows (before Ubuntu) I was able to use smartFTP and download all day long.  So I guess I need some basic instructions.

I am trying to download Grateful Dead shows from 
[http://ia301109.us.archive.org/1/items/gd94-10-14.sbd.perkins.9054.sbeok.shnf/](http://ia301109.us.archive.org/1/items/gd94-10-14.sbd.perkins.9054.sbeok.shnf/)   (this should be all one string)

Usually I enter ia301109.us.archive.org into the Host 
I use anonymous for username and connect.
When it works I get a view into what is in ia301109.us.archive.org which is
always /0 /1 /2 and /3
I can proceed down the list to find the specific show I'm interested in downloading and it will display all the files that are there.

Can someone direct me to some reading material to help me understand how to use these FTP programs properly?  Like beginner material?
Thanks in advance.
Stephen

---

### Post by tuxxy on 2008-10-14
Why use an FTP program, you could use nautilus (your file explorer window) and type this in the address bar

```
ftp://ia301109.us.archive.org/1/items gd94-10-14.sbd.perkins.9054.sbeok.shnf
```

Now drag and drop them to your desktop :)

---

### Post by oldos2er on 2008-10-14
HTTP and FTP protocols aren't interchangeable. You can use wget to grab http files; or a simple web browser.

---

### Post by swbrenton on 2008-10-14
> **tuxxy said:**
> Why use an FTP program, you could use nautilus (your file explorer window) and type this in the address bar

```
ftp://ia301109.us.archive.org/1/items gd94-10-14.sbd.perkins.9054.sbeok.shnf
```

Now drag and drop them to your desktop :)

I tried it.  It doesn't work.  See attached.  Does it work on your computer?  :(

---

### Post by swbrenton on 2008-10-14
> **oldos2er said:**
> HTTP and FTP protocols aren't interchangeable. You can use wget to grab http files; or a simple web browser.

I don't know what HTTP or FTP protocols are. :confused:
I don't know what you mean by use wget.       :confused:
I don't know how to use a simple web browser to download these files.  :confused:



I would prefer an answer from someone who knows how to use gFTP or FireZilla.  Or direct me to where I can read how to use.

---

### Post by Mister.Vash on 2008-10-14
I may be missing something here...  In your first post, you reference the site:
[http://ia301109.us.archive.org/1/items/gd94-10-14.sbd.perkins.9054.sbeok.shnf/](http://ia301109.us.archive.org/1/items/gd94-10-14.sbd.perkins.9054.sbeok.shnf/)

When I clicked on the link in your post it took me to a page, and I was able to start downloading a file by right clicking on one and then choosing save link as and it proceeded to download and save the file.

Are you looking to use a different program rather than a browser to download these files, or are you having trouble downloading them via a browser like firefox?

---

### Post by oldos2er on 2008-10-15
> **swbrenton said:**
> I don't know what HTTP or FTP protocols are. :confused:
I don't know what you mean by use wget.       :confused:
I don't know how to use a simple web browser to download these files.  :confused:
  

 The link you provided ([http://ia301109.us.archive.org/1/items/gd94-10-14.sbd.perkins.9054.sbeok.shnf/](http://ia301109.us.archive.org/1/items/gd94-10-14.sbd.perkins.9054.sbeok.shnf/)) starts with http:, hypertext transfer protocol. The programs you're trying to use, gftp and filezilla, are made to use FTP, or file transfer protocol. The two are not compatible. wget is a CLI program that can download using either ftp or http.

---

### Post by niteshifter on 2008-10-15
Hi,

Being a Dead Head this caught my eye .... I believe I can clear up some things:

Problem with this file - complete URL given below - is a permissions problem at the site.
ia301109.us.archive.org/1/items/gd94-10-14.sbd.perkins.9054.sbeok.shnf/gd94-10-14d1t01.ogg

Shows all perms set to off. This via gFTP. Gives a permissions denied error. Also same via cli ftp - no surprise as gFTP is just a GUI front for /usr/bin/ftp.

The site traps http request and gives an error page (in HTML) - which if one clicks "Save Link As" will dutifully save it as .ogg -- but what you're getting is not ogg data, it's HTML (open it with a text editor to see this).

Snippet from said html:
```
<div id="col2">
  <div class="box">
  <h1>Item not available</h1>
  The item is not available due to issues with the item's content.
</div>

```

What is curious is all the .ogg and <filename>_64kb.mp3 files are set this way. Only the files <filename>_vbr.mp3 are downloadable. Listening to gd94-10-14d1t01_vbr.mp3 (Jack Straw) as I write this.

To the OP: gFTP works but sometimes the trick for anonymous logins is to set options first. Click FTP on gFTP's main menu, then click Options. In the dialog that appears, click the FTP tab - make sure that there is a valid looking email address present. It  doesn't have to be a valid email, [email]joeblow@example.com[/email] will work. 
Now, enter the site URL in Host, anonymous for User and press enter. gFTP should log you in if the site supports anon logins.

---

### Post by swbrenton on 2008-10-15
> **Mister.Vash said:**
> I may be missing something here...  In your first post, you reference the site:
[http://ia301109.us.archive.org/1/items/gd94-10-14.sbd.perkins.9054.sbeok.shnf/](http://ia301109.us.archive.org/1/items/gd94-10-14.sbd.perkins.9054.sbeok.shnf/)

When I clicked on the link in your post it took me to a page, and I was able to start downloading a file by right clicking on one and then choosing save link as and it proceeded to download and save the file.



Hello Mister.Vash-
I didn't know I could download that way.  (i.e. When I clicked on the link in your post it took me to a page, and I was able to start downloading a file by right clicking on one and then choosing save link as and it proceeded to download and save the file.)

This works for .mp3 files.  For some reason it will not work for .ogg files.  Oh well.  I can work with the .mp3 files.

> **Mister.Vash said:**
>  Are you looking to use a different program rather than a browser to download these files, or are you having trouble downloading them via a browser like firefox?

I was looking for a way to download and thought I had to use a FTP program to do it.  I didn't know I could use the technique you described.  When I attempted to use gFTP or FireZilla I could not get the program to connect to the host.  So I was asking for help in what has to be entered and where in order for the FTP program to start working.

When you look at the list of files displayed when you click on the link in my post you see four different versions of each song track.  i.e. .mp3, .ogg, etc.
The FTP program I was using in windows (smartFTP) allowed me to select only the *vbr.mp3 files and move them into the download que.  That was nice.  That will be my next challenge.

Thanks for your help.
Stephen

---

### Post by mikjp on 2008-10-15
Use [wget](http://lightlinux.blogspot.com/2008/08/cli-download-iso-images-with-wget.html) for downloads on command line. Even more information [here](http://lifehacker.com/software/downloads/geek-to-live-mastering-wget-161202.php).

---

### Post by swbrenton on 2008-10-15
> **niteshifter said:**
> Hi, 
Being a Dead Head this caught my eye .... I believe I can clear up some things:

Thanks for looking into this for me.  Lots of good music where this came from. 


> **niteshifter said:**
> 
Snippet from said html:
```
<div id="col2">
  <div class="box">
  <h1>Item not available</h1>
  The item is not available due to issues with the item's content.
</div>

```

I'm not sure what the above snippet of code says.  I'm going to look and think some about it.  Were you looking at the page's source?



> **niteshifter said:**
> Hi,
What is curious is all the .ogg and <filename>_64kb.mp3 files are set this way. Only the files <filename>_vbr.mp3 are downloadable. Listening to gd94-10-14d1t01_vbr.mp3 (Jack Straw) as I write this.

Yes.  I found out the same thing when I attempted to download the *.ogg files from the browser as Mister.Vash showed me earlier.  But *vbr.mp3 are downloadable.  OK, I can deal with that.


> **niteshifter said:**
> 
To the OP: gFTP works but sometimes the trick for anonymous logins is to set options first. Click FTP on gFTP's main menu, then click Options. In the dialog that appears, click the FTP tab - make sure that there is a valid looking email address present. It  doesn't have to be a valid email, [email]joeblow@example.com[/email] will work. 
Now, enter the site URL in Host, anonymous for User and press enter. gFTP should log you in if the site supports anon logins.

Now we're talking.  Now gFTP works for me.  Simple answer.  Thank you.
Stephen.

---

### Post by swbrenton on 2008-10-15
> **mikjp said:**
> Use [wget](http://lightlinux.blogspot.com/2008/08/cli-download-iso-images-with-wget.html) for downloads on command line. Even more information [here](http://lifehacker.com/software/downloads/geek-to-live-mastering-wget-161202.php).

Looks interesting and promising.  I'll have to play with it some.
Thanks
Stephen.

---

