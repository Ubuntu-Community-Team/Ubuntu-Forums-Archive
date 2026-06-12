---
title: "Binary Data over RS-232 using minicom"
date: 2008-11-21
forum: General Help
---

### Post by maltomario on 2008-11-21
My apologies if this is not the correct forum to post this, but...

I am working with a piece of hardware (remote sensor) that outputs binary data instead of ASCII.  When I try to use minicom, and set to proper comm paramaters, I get 'garbage' data on the terminal screen.  By 'garbage' I mean non-ascii characters.

I am using a USB to serial converter which I know to be working properly from other tests.

I get this same consistent behavior in windows hyperterminal, but there appears to be at least a couple different terminal programs for windows that support binary communication.  For example, 

I have not had luck configuring minicom to work in this application, nor have I found a terminal app (linux) that will handle binary.

have any of you run into a problem like this?  Any suggestions?  Thanks in advance.

---

### Post by ModelM on 2008-11-21
Obviously the data cannot be properly represented on the screen, so what exactly do you want to do with it? If you want to save it to a file as it is received, you might find that cutecom meets your needs better than minicom.

Cutecom was designed specifically for the type of device communication you are doing, and it will display the output in hexadecimal if you choose.

---

### Post by maltomario on 2008-11-21
its a sensor so I will be reading data continuously and processing it as I see fit.  It is streaming so I can't just save it to a file as you suggested.  Thanks for the suggestion for cutecom.  i will look into it.

but, I think I will most likely end up having to write my own program to read the data from ttyUSB0

---

### Post by maltomario on 2008-11-24
can anyone recommend good reading material / examples for how a noob like me can start writing a program to read serial data (binary) from a comm port in linux?

---

### Post by ModelM on 2008-11-24
The easiest route for you would probably be to grab the source code for minicom, cutecom, or whatever terminal program you like and simply add one or two lines to add 0x30 to the value of each bit of the incoming data. A set bit would then display as "1" and a clear bit would display as "0".

There would be no formatting but it sounds like this is what you want.

---

### Post by maltomario on 2008-11-24
ok admittedly I'm a noob...so please go easy on me.

so if i have these programs installed (as it turns out i do have both minicom and cutecom installed on my ubuntu 8.04 Hardy Heron box) how do i know if I have the source code or not?  Where is this source stored?  I realize this seems like a trivial question for you seasoned pros...

in my /usr/bin directory I see executable for cutecom and minicom but where is the source code?  Do i need to download source separately (ie is it not installed by default when using the "sudo apt-get install..."?

thanks in advance for any help. Thanks also for the patience to answer so many questions from people like me seeking to improve their understanding.

---

### Post by decard_pain on 2008-11-24
if you didn't compile it from source then you don't have the source.you need to download it from there site...where ever that is

---

### Post by ModelM on 2008-11-24
You should be able to ge the source by simply opening Synaptic, go to settings, repositories & enable "source code". Or these might be listed in the "third party" tab since they are not Ubuntu supported packages, so you should enable "source code" there, as well.

After refreshing Synaptic you should see the source code package listed in Synaptic.

---

### Post by The Cog on 2008-11-24
I don't see a need to dig through the minicom source. You need to be able to call **stty** to configure the port for the right speed and parity settings etc, and you need to be able to open /dev/ttyUSB0 as a file for reading. Both of these are possible in many languages. What language did you have in mind?

---

### Post by maltomario on 2008-11-24
Thinking about coding in C, only because thats what I have most experience with.

---

### Post by The Cog on 2008-11-24
In that case, you might find the source code interesting. But I still think you only need stty and open. I think they're both C library calls.

---

### Post by maltomario on 2008-12-04
Cog, thanks for the suggestion but I believe using stty() will incur a significant time delay and therefore may be unsuitable for this application.

---

### Post by tzeronone on 2012-12-20
Has this problem been solved?

---

### Post by lisati on 2012-12-21
> **tzeronone said:**
> Has this problem been solved?

Raising threads from the dead is something that is best dealt with elsewhere, particularly when they haven't had a response for four years: a lot has changed in that time.

If you're having a similar problem, please start a new thread, linking back to this one if necessary.

---

