---
title: "Stream WebCam To WebServer (tried a few different things)"
date: 2010-11-23
forum: Hardware
---

### Post by usopenplayer on 2010-11-23
Hey Guys,
  I am leaving my apartment for Thanksgiving and I wanted to set up a few web cams that stream video to a web server that I have, so that I can keep tabs on my stuff.

I have tried using the program motion; however, the lightweight http server that comes with it is too lightweight for the functionality that would be ideal, yet too complicated for me to take full control of the web cam and do my own stuff with it.

So, I figured that I could just run something like: ```
sudo cat /dev/video0 | nc -l 1337
``` and point my webserver to home IP address.

Unfortunately I seem to be getting "cat: /dev/video0: Invalid argument"
I looked online for solutions, but everyone who has this problem is trying to get their webcam working in the first place. Other programs such as Skype can access my webcam just fine. What am I doing wrong?

```
lsusb | grep Webcam
``` returns: Bus 001 Device 006: ID 17ef:480f Lenovo Integrated Webcam [R5U877], so my camera is being detected just fine... I just can't access it from the terminal!

If someone knows of any programs that are better than motion, that would be appreciated, but I also really want to find out how to access my devices from the terminal.

For the record, I don't really need motion detection, I just want to be able to tune into the video.

---

### Post by Fafler on 2010-11-23
You could make a shell script that takes a shot every n seconds and place it in /vat/www and a small client side script that reloads the page. I did that once.

---

### Post by usopenplayer on 2010-11-24
Although I couldn't find out why I can't cat out my /dev/video0 file, I did end up getting motion to work.

The config file for motion located at /etc/motion/motion.conf had a first line entry that I misread. By default motion is not run in daemon mode. Tweeking frames per second was simple enough.

On my Web Server I just added simple image tag with the ip address of the motion http server.
<img src="http://192.168.1.50:8081" alt="Camera" />

---

### Post by usopenplayer on 2010-11-24
> **Fafler said:**
> You could make a shell script that takes a shot every n seconds and place it in /vat/www and a small client side script that reloads the page. I did that once.

I almost did this, definitely useful for future stuff that I have in mind, but I ended up getting motion to work, which sufficed for this project. Thanks for your input!

---

