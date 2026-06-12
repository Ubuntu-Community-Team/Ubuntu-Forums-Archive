---
title: "Gps and navigation"
date: 2010-10-11
forum: Hardware
---

### Post by kkaldroma on 2010-10-11
I know this topic has been hit quite a bit but the last good update I saw was from 2008 (its 2010 now)

My questions are:

Is there a way to get GPS coordinates command line ( i have tired and failed miserable using gpsd ) 

Is there a good turn by turn navigation system using a usb-gps.
 
I have tried streets and trips via WINE and Vbox and again failed, I have tried GPSdrive (doesn't want to recognize my usbGps), I have tried Navit (refused to work with any maps), I have tried togo (also refused my GPS).

I am using a navibe GPS receiver and would love to get it to work with my asus G50v.

Any help is appreciated.

---

### Post by IcarusR on 2010-10-13
> Is there a way to get GPS coordinates command line ( i have tired and failed miserable using gpsd ) 

Use gpsd to get info from gps & gpspipeline to print info to screen. I get this...

```
$ gpspipe -w -n 100
GPSD,X=1286964345.812508,I=Generic NMEA
GPSD,W=1,A=?,T=?,C=1.00,E=?,N=0,A=?,B=57600 8 N 1,L=3 1 2.39 abcdefgijklmnopqrstuvwxyz,E=?,T=?,R=1,U=?,E=?,J=0,S=1,O=?,N=0,T=?,R=0,U=?,E=?
GPSD,O=GGA 1286964345.440 0.005 **.036755000 -0.804880000 93.500 18.750 40.250 ? ? 0.000 ? ? ? 3
GPSD,O=GSA 1286964345.440 0.005 **.036755000 -0.804880000 93.500 18.750 40.250 ? ? 0.000 ? ? ? 3
GPSD,O=GLL 1286964345.440 0.005 **.036755000 -0.804880000 93.500 18.750 40.250 ? ? 0.000 ? ? ? 3
GPSD,O=RMC 1286964345.440 0.005 **.036755000 -0.804880000 93.500 18.750 40.250 0.0000 0.000 0.000 ? ? ? 3
```

**.036755000 -0.804880000 is my position, first two numbers I have substituted **

> I have tried GPSdrive (doesn't want to recognise my usbGps)

I had the same problem. GPSdrive uses gpsd to read gps stream. I believe that the version of gpsd in the lucid repos is not compatable with the version of  GPSdrive. 
I downgraded gpsd to the Intrepid version, 2.39, now works OK.

> I have tried Navit (refused to work with any maps)

I tried Navit & got p*^%$£ off trying to get various maps to work, encluding my unlocked garmin maps. Gave up.

> I have tried togo (also refused my GPS)

I assume you mean Tango ? Possibly same as above, but defiantly works with gpsd 2.39. Tango works, good openstreetmaps, but does not do voice directions.

Limited on maps here in UK. There are conciderably more free maps available in US.

---

### Post by kkaldroma on 2010-10-13
Thank you for your reply. 

I did mean tango, I don't know why I had it stuck in my head that it was called togo, either way it didn't work before but I'll try it again.

Rolling back to gpsd 2.39 and installing libgps18_2.39-5 got everything up and running.

I do get a strange "GPGGA: wrong number of fields (14)" error scrawling through my terminal but I get accurate GPS locations.

---

### Post by IcarusR on 2010-10-14
Glad it helped.

> Rolling back to gpsd 2.39

You will need to 'pin' it to that version in synaptic to prevent updates from updating it to latest version.

In synaptic search for gpsd, hilite it then go to package menue & select 'lock version'.

---

### Post by nutznboltz on 2011-01-30
There is a bug report filed in Launchpad regarding the GPSdrive/gpsd compatibility issue with Lucid.

[https://bugs.launchpad.net/ubuntu/+source/gpsdrive/+bug/585025](https://bugs.launchpad.net/ubuntu/+source/gpsdrive/+bug/585025)

---

### Post by nutznboltz on 2011-01-30
I've started working on a PPA for gpsdrive on Lucid.

So far I've got this:

[https://launchpad.net/~nutznboltz/+archive/gpsdrive](https://launchpad.net/~nutznboltz/+archive/gpsdrive)

---

### Post by nutznboltz on 2011-01-31
Trying to port to Maverick crashes into the deletion of the libtext-query-perl package:

[https://launchpad.net/ubuntu/maverick/+source/libtext-query-perl/0.07-4](https://launchpad.net/ubuntu/maverick/+source/libtext-query-perl/0.07-4)

I suppose I can forward-port it from Lucid and add it to the PPA but *sheesh*

---

### Post by nutznboltz on 2011-01-31
The PPA builds on Maverick 10.10 now.  I went back and adjusted the build-depends in the lucid packages to include the perl stuff too.

---

### Post by Herman on 2011-02-22
> Is there a way to get GPS coordinates command line ( i have tired and failed miserable using gpsd ) The following command should give you your latitude. longitude and elevation,
```
gpspipe -w -n 5 | grep lat | cut -d ":" -f6,7,8,9 | cut -b 13-22,33-42,53-55
```If you want to have those broken down into separate values, you can use the following lines as part of a bash script,
```
lat=$( gpspipe -w | grep -m 1 lat | cut -d ":" -f6,7,8,9 | cut -b 13-22 )
lon=$( gpspipe -w | grep -m 1 lat | cut -d ":" -f6,7,8,9 | cut -b 33-42 )
alt=$( gpspipe -w | grep -m 1 lat | cut -d ":" -f6,7,8,9 | cut -b 53-55 )
echo " 
          Your current position is "$lat", "$lon", "$alt"
       "
```If you make yourself a bash script, you have those coords echoed to a file, and you can set up categories for the features you want to record along with each set of coordinates for display in your map. You might want to set up your script with multiple choices something along the lines of what is exemplified in the following link, [Flow Control Part2]("http://linuxcommand.org/wss0120.php").
For example,
```
PS3="Please type a number between 1 and 9 for the word which best describes this landmark (1-9):"
select typ in hill homestead windmill bore well stockyard gravelpit waterpoint other
do
      break
done
echo " 
                                     $typ
        "
```Then you could get your script to run you through a short series of prepared questions where you just need to press a number and your enter key to record attributes and have the data written to a .csv file, which of course you can open with your mapping program and/or gnumeric spreadsheet for editing if needed. :)

---

### Post by hemlockz on 2011-02-27
^ This was very helpful to me too, thanks Herman

---

### Post by janmartin on 2011-03-13
Hi all,

I need to display the time from GPS, but screen-filling, not just in Terminal. So one can read it from a distance.

How would one do that?

Thank,
Jan

---

### Post by Herman on 2011-03-15
:D Hello Jan,
The following code is only one step towards doing what you asked, and at least it's better than nothing.

First, we tell the terminal to find out what day today is,
```
now=$(date +"%a %b %d")
```Now, we tell gpspipe to run with the -t option to put in the timestamps, and use grep will watch for every instance of today's date, (stored in the variable "$now"), which will always be followed by the time. We use the cut command to cut out the time,
```
gpspipe -w -t | grep "now" | cut -b 12-19
```:rolleyes: It's a little jerky, but it does at least output the current time from satellites in a stream running down the terminal window. Mine works in fits and starts.

An idea might be to make up some other script and get it to synch the system clock every once in a while and run a clock widget from that. I used to use some kind of a software clock that I used to be able to get to fill my screen. I am trying to remember the name of it but I can't recall right now. 

If you have an internet connection I'm not sure this would be any more accurate than getting the time from an internet time server though. 
If we go 'System', 'Administration','Time and Date', and 'click to make changes', (on the padlock icon), then select 'keep synchronized with internet servers', and install NTP support we should have the most accurate time in our system clock already.

There could be special reasons why a person might want to get the time from satellites though, I'm not sure. Anyway, I hope this helped you a little.  :)

---

