---
title: "Problem with wget and putting a job in the background"
date: 2008-08-18
forum: General Help
---

### Post by maxbaroi on 2008-08-18
I tried putting a job in the background. Instead it went to the foreground but it behaved like a background job, that is, I couldn't stop it using ctrl-z. 

The following is what I typed into the terminal, along with my comments in italic.


max@max:~$ wget [http://download.gamevideos.com/Podcasts/Download/gv.com.1upshow.0909_640x360.wmv](http://download.gamevideos.com/Podcasts/Download/gv.com.1upshow.0909_640x360.wmv)
--01:20:24--  [http://download.gamevideos.com/Podcasts/Download/gv.com.1upshow.0909_640x360.wmv](http://download.gamevideos.com/Podcasts/Download/gv.com.1upshow.0909_640x360.wmv)
           => `gv.com.1upshow.0909_640x360.wmv.4'
Resolving download.gamevideos.com... 38.102.128.194
Connecting to download.gamevideos.com|38.102.128.194|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 446,590,663 (426M) [application/octet-stream]

 0% [                                     ] 19,320         6.51K/s             

*...everything fine, I type ctrl-c...*

[1]+  Stopped                 wget [http://download.gamevideos.com/Podcasts/Download/gv.com.1upshow.0909_640x360.wmv](http://download.gamevideos.com/Podcasts/Download/gv.com.1upshow.0909_640x360.wmv)

*...the job stops as it should...*

max@max:~$ jobs
[1]+  Stopped                 wget [http://download.gamevideos.com/Podcasts/Download/gv.com.1upshow.0909_640x360.wmv](http://download.gamevideos.com/Podcasts/Download/gv.com.1upshow.0909_640x360.wmv)

*...the job's still there as it should be...*

max@max:~$ bg 
[1]+ wget [http://download.gamevideos.com/Podcasts/Download/gv.com.1upshow.0909_640x360.wmv](http://download.gamevideos.com/Podcasts/Download/gv.com.1upshow.0909_640x360.wmv) &
 0% [                                     ] 56,404         5.46K/s ETA 22:12:11m 0% [                                     ] 299,460       19.32K/s  ETA 7:27:22fg
wget [http://download.gamevideos.com/Podcasts/Download/gv.com.1upshow.0909_640x360.wmv](http://download.gamevideos.com/Podcasts/Download/gv.com.1upshow.0909_640x360.wmv)
 0% [                                     ] 426,420       23.75K/s  ETA 5:41:01
[1]+  Stopped                 wget [http://download.gamevideos.com/Podcasts/Download/gv.com.1upshow.0909_640x360.wmv](http://download.gamevideos.com/Podcasts/Download/gv.com.1upshow.0909_640x360.wmv)

[I]...The above is where things got stupid. I enter bg, but the job is clearly put into the foreground. But it's not even as simple as that, because ctrl-z doesn't stop the job. I first have to enter fg (you can see fg right after ETA 7:27:22), and then I'm able to stop it with ctrl-z. What's even stranger is that everything worked as it should when I tried a different command such as"sleep 999".
I'm a bit stumped...[/I]  

max@max:~$ jobs
[1]+  Stopped                 wget [http://download.gamevideos.com/Podcasts/Download/gv.com.1upshow.0909_640x360.wmv](http://download.gamevideos.com/Podcasts/Download/gv.com.1upshow.0909_640x360.wmv)
max@max:~$ 



Any help would be appreciated. I run 8.04 and this was done on the gnome-terminal, but I get identical results on xterm and konsole.

---

### Post by amo-ej1 on 2008-08-18
When you typed bg, the job was still running in background, but wget was simply still showing output with got to your console. Putting a job in background really means that you can get control back (if you would type ls you would see ls output). 

So you question is, how do I put wget in background without seeing the progress on my screen. 

```

edb@lapedb:/tmp$ wget --quiet http://www.google.com & 
[1] 11412
edb@lapedb:/tmp$ 
[1]+  Done                    wget --quiet http://www.google.com

```

Then simply pass the --quiet option to wget. And it will inform you when the download has finished.

This behaviour is bash default, and using konsole, xterm, ... or any other terminal emulator will not make any difference.

---

### Post by maxbaroi on 2008-08-18
Thank you.

---

