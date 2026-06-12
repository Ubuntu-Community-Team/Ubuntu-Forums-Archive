---
title: "OBDII Code Readers COM1 Port"
date: 2009-09-12
forum: Hardware
---

### Post by gcvisel on 2009-09-12
Anybody out there know how to get Scantool or similar OBD-II automotive troubleshooting code readers to work on Ubuntu?  I downloaded Scantool and ran it under WINE, but it had a popup that it could not find COM1 port and allowing me to choose among COM1 to COM10, but it didn't recognize any of them.  The code reader I got has a USB input to a laptop and comes with the Scantool and other such software, but I can't get it to see the tool.

Any ideas?

Thanks!
Gerry

---

### Post by bregale on 2009-09-12
hi i cant help you with your scantool  but your post has helped me a bit as i am hoping to do the same as you ,i have some software we use at work for diagnosis and i want to run on linux but cant get any helpful answers if i do i will pm you 
    cheers

---

### Post by gcvisel on 2009-09-12
> **bregale said:**
> hi i cant help you with your scantool  but your post has helped me a bit as i am hoping to do the same as you ,i have some software we use at work for diagnosis and i want to run on linux but cant get any helpful answers if i do i will pm you 
    cheers
I did find this:
[https://www.scantool.net/forum/index.php?action=printpage;topic=3086.0](https://www.scantool.net/forum/index.php?action=printpage;topic=3086.0)
but still can't quite get them to talk to each other...

... Oh, and the COM ports offered were 1 through 8, fwiw.
Gerry

---

### Post by gcvisel on 2009-09-13
I don't have any working  yet, but check out:
[http://forums.speedguide.net/showthread.php?t=247979](http://forums.speedguide.net/showthread.php?t=247979)
which has lots of possibilities...

Gerry

---

### Post by gcvisel on 2009-09-21
YESSS!!!

What ya gotta do is:
1.  Make a link from your USB port to a Com port:
```
ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com5
```...or another unused Com port number.

Then check that it took:
```
ls -l ~/.wine/dosdevices/
```(Important!)  Then authorize access:
```
sudo chmod 0777 /dev/ttyUSB0
```Then plug 'er in and go!

I downloaded the latest copy of Scantool from:
[http://www.scantool.net/scantool/downloads/diagnostic-software/](http://www.scantool.net/scantool/downloads/diagnostic-software/)
I'm running version 114, but I saw 115 just came up.

Then, with the OBDII tool plugged into the car and your USB port and the car switch in the ON position, either running or not, start ScanTool.  It will pop up a dialog box to "Configure Port."  I chose COM5 and 38,400 baud rate, with US measurements and a Windowed screen, which it finally accepted.

Back to the Main Menu and you can now read and reset codes, and watch 8 pages of sensor data real time.  (Lots of them were N/A on my '97 GMC pickup truck.  I'm sure it will now work on my '08 Prius.

Oh yeah.  I think all the code listed above is remembered for your next session except for that last access authorization statement.  I'll try to figure a way to put that into a shortcut so I can just hit a button to authorize.

Have fun!

Gerry

---

### Post by johnvan on 2010-04-06
Great Post.  Just picked up one of these on Ebay and it was easy to set up thanks to this post.

---

### Post by I got worms. on 2010-06-21
I'm having some issues with setting up my OBDII scanner and I feel like it's something small that I must be overlooking. 

I have wine installed but it won't allow me to open up Scantool. I get a blocked wine start window saying that the scantool file 120 is not an executable file.  

How can I get around this?

---

### Post by koshari on 2010-07-07
you will need to set its properties as executable iam guessing.

in nautilus, select the file, go to properties > permissions tab  and insure the "allow executing file as a program" radio box is checked

---

### Post by Carl Farrington on 2010-08-01
> **koshari said:**
> you will need to set its properties as executable iam guessing.

in nautilus, select the file, go to properties > permissions tab  and insure the "allow executing file as a program" radio box is checked

igotworms forgot to say thanks, so, thanks from igotworms ;)

---

### Post by Andre-D on 2010-08-11
please correct me if I am wrong, but in newer Ubuntu's , liek 10.04, there's no need for 
"sudo chmod 0777 /dev/ttyUSB0"

- because dialout group already have read+write permissions .. (?)

---

