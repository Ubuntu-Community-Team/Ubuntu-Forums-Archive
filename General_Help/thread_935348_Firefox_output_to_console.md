---
title: "Firefox output to console"
date: 2008-10-01
forum: General Help
---

### Post by alberto ferreira on 2008-10-01
I have a script to download youtube files:


```
#! /bin/bash
if [ -f /tmp/Flash* ]; then
#Watch file
#totem --enqueue /tmp/Flash*
cp -i /tmp/Flash* ~/Vídeos/"$1".flv
else
echo "File doesn't exist or there is more than one flv open"
fi
echo "Done"
exit
```That script downloads the flash video however I'm tired of writing the name of the video over and over, so, here's what I wanted to do.

Have firefox save the current page so that I could then with a script isolate the name of the video from the html code and use it to name my file.
However I'm using bash so I don't know how to do this. Is there any option in firefox to output the content of the current page or it's HTML code?
I'd really love to have this working.

---

### Post by ibuclaw on 2008-10-01
Hmm...

Not sure on the legality of this question. youtube tends to be iffy when it comes to people downloading content to watch offline.

You can resort to programming languages, such as Perl for this.
Perl is very good at cutting and extracting data from webpages.

There is also **curl** which gets the page source and dumps it to stdout.

Iain

---

### Post by alberto ferreira on 2008-10-02
Need some help, I'm in trouble :$

1-I don't know any programming language for pc
2-curl must be fed an url however I would need to copy the url from firefox when I wanted a script that would just need to be executed and would gather all the information by itself.

---

### Post by alberto ferreira on 2008-10-05
Thanks, I am now using curl as you suggested, but I would like to know how I can find the last URL in firefox 3 to download the page source in real time and find the name of the video instead of having to paste the URL into the console.
This is the script that I'm currently using:
[http://ubuntuforums.org/showthread.php?t=937903](http://ubuntuforums.org/showthread.php?t=937903)

The places.sqlite is the file where firefox saves this info but with sqlite3 when I want to open the file the folloiwing message is printed:
> Unable to open database "places.sqlite": file is encrypted or is not a database

How do I open it and convert it to a text file?

Or is there an easier way to do this?


Should the post be moved to Programming talk section? If that's the case someone tell me how because I don't know how to do that.

---

