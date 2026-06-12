---
title: "Low power Ubuntu home server"
date: 2015-10-11
forum: Hardware
---

### Post by JohnyBeGood on 2015-10-11
[COLOR=#222222][FONT=Verdana]Hi all,[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]I would like to build [/FONT][/COLOR]_low power _[COLOR=#222222][FONT=Verdana]Linux server and install Ubuntu on it.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Primary purpose on it to learn about Linux and second one is to store my home Hikvison IP-Camera surveillance footage there and also use for personal picture/video backup.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Now I have small Acer Aspire Revo AR1600 that has 250GB hard drive and runs Elastix on it (1 slot only). Using samba I have allocated only 50GB and as it fills up it deletes older footage automatically. [/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]My goal is to buy NAS rated HD and have bigger storage capabilities. [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]I did lots of research online and closest and most recent article that I came across is this one [/FONT][/COLOR]
[https://anteru.net/2015/01/19/2678/](https://anteru.net/2015/01/19/2678/)
[COLOR=#222222][FONT=Verdana]I like everything about setup but on last page [/FONT][/COLOR][https://anteru.net/2015/01/25/2724/](https://anteru.net/2015/01/25/2724/)[COLOR=#222222][FONT=Verdana] it lists that power consumption is 28-29W? I think that's a lot for setup build in 2015, am I wrong?[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]Any suggestions or recommendations will be greatly appreciated![/FONT][/COLOR]

---

### Post by mastablasta on 2015-10-12
heh the builder goes through the trouble of getting ECC RAM and then get's the cheapest?!?! also I don't think ECC is necessary but it is recommended.

depends on what you want and what server does when "idle". RaspberyPi will consume a lot less power but is limited in features.

I got one of HP Microservers. I never tested the power consumption, but it should be around those numbers. 2 disk will take 8-10 w. with raid when they run, both are running. like I said if you go cheap you will have some limitation (either in speed/performance or something else). you could also get a premade NAS. they have lower power consumption. but i think it's still between 15 and 20 W.

---

### Post by JohnyBeGood on 2015-10-13
> **mastablasta said:**
> heh the builder goes through the trouble of getting ECC RAM and then get's the cheapest?!?! also I don't think ECC is necessary but it is recommended.

depends on what you want and what server does when "idle". RaspberyPi will consume a lot less power but is limited in features.

I got one of HP Microservers. I never tested the power consumption, but it should be around those numbers. 2 disk will take 8-10 w. with raid when they run, both are running. like I said if you go cheap you will have some limitation (either in speed/performance or something else). you could also get a premade NAS. they have lower power consumption. but i think it's still between 15 and 20 W.

Thanks for the reply!

When "idle" server wouldn't anything other then wait for motion detection of IP camera and store that footage.
Instead of going premade route I would like to build it my self with nice small expendable case.

---

### Post by Bucky Ball on 2015-10-13
> **JohnyBeGood said:**
> power consumption is 28-29W? I think that's a lot for setup build in 2015, am I wrong?

I'd say so. You are talking about a box with probably or 450+ watt PSU in it, and that may be a generic silver box PSU. Go for an 80+ PSU if you go down that track and _avoid generic silver box PSUs_ at all costs. 

An [Odroid]("http://www.hardkernel.com/main/main.php") should do what you want with a hard drive or two hanging off it.

---

### Post by mastablasta on 2015-10-13
if all you need it for is "security system" then I would go with RPi (or something similar) as it can fit into a small box together with drive. you could somehow mirror the drives or at least use one drive as backup or something. check out their forums for suggestions. many attached a small solar panel and added some rechargeable battery pack or a Li-ION battery. That way the system is self sustained. in case of power outage it could still record for hours since it needs so little power to run. the downside may be that I am not sure if there are any good external hard drives, though you could always get a purple drive (they are meant for video /security recordings) and put it in external enclosure.

but anyway it is hard for me to say what to do, since I am not an expert in this kind of stuff.

---

### Post by Yellow Pasque on 2015-10-13
> **JohnyBeGood said:**
>  it lists that power consumption is 28-29W? I think that's a lot for setup build in 2015, am I wrong?

It's not out of the ballpark. More recent chips (Bay Trail or Braswell) will shave some of that off. Personally, I'd look at boards like: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813157653](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157653)

> You are talking about a box with probably or 450+ watt PSU in it

If we're talking about <60W, a power brick or picoPSU will suffice. No need for a full box PSU, especially with a motherboard that accepts a DC power source.

---

### Post by matt_symes on 2015-10-13
Hi

I am currently in the process of playing wth a new raspberry pi and zoneminder with the intention of running 4/5 camera at a low fps of around 4 and a external hard drive hanging of the side for recording.

If zoneminder is too heavy, I'll look into motion. This is to replace a Windows 7 PC running ispy.

As it's looking at the moment, I may have to use 2; one for the backend and one for the front end browser that will be connected to either a tv or a monitor using the hdmi connection.

I've been considering running either the backend using an odriod c1.

It'll be pretty low powered if it runs well enough.

You never mentioned how many camera's you are trying to run. I'll post back how I get on.

Kind regards

---

### Post by Bucky Ball on 2015-10-13
> **Temüjin said:**
> No need for a full box PSU ...

Totally agree. I'd go the Odroid, as mentioned. I assumed, probably wrongly, the OP was talking about a regular box. :D

---

### Post by matt_symes on 2015-10-13
Hi

Well the raspberry pi has the grunt to stream the three watchbot cameras to a Linux laptop. I'm using mjpeg for that and the cameras snapshot api.

The escam camera (peashooter) is an rtsp camera and I can only view the stream on from that camera in zoneminder using the ffmpeg plugin and that is chewing up CPU cycles.

The version of zoneminder in that pi repositories is at version v1.25 and so is way behind v1.28 and does not have the libvlc plugin that may perform better. Maybe trying to build a newer version may be the way to go.

This will need to be very optimised to work with the four cameras and I have not even tried motion detection with all four camera to the hard drive yet, to check for I/O issues. Then, of course, there's stability testing.

It's Ethernet connected as the wireless was useless.

An odriod c1 may be the way to go if zoneminder is in the repos due to its much faster chip.

Either way, I just love these little boards.

Kind regards

---

### Post by JohnyBeGood on 2015-10-14
Thanks for the replies guys!

My Hikvision DS-2CD2032-I already has web interface and does not need Zoneminder. All what it needs is somewhere to store footage when motion is being detected.
You can check out the review here [http://www.networkcameracritic.com/?p=1444](http://www.networkcameracritic.com/?p=1444)

I did not mention it in my initial post but I really want to use desktop version of Ubuntu and I don't think ODROID or Raspberry pi would be able to handle it?

Looks like I need to change my view and accept that low power use machine can't handle everything.
I came across this home server Lenovo ThinkServer TS140 Tower Server System Intel Xeon E3-1225 v3 3.2GHz 4GB [http://www.newegg.com/Product/Product.aspx?Item=N82E16859106529](http://www.newegg.com/Product/Product.aspx?Item=N82E16859106529)
and its power consumption is 30-35Watts with 1 SSD as boot. Each additional ie. WD RED adds another 5W. I gathered it by reading users reviews.

It's also on certifed for Ubuntu list
[http://www.ubuntu.com/certification/hardware/201504-18149/](http://www.ubuntu.com/certification/hardware/201504-18149/)

---

### Post by mastablasta on 2015-10-14
if you are ok with power consumption it will be fine. probably an overkill ;)

you do not need full desktop if you can control things via browser (GUI). even if you do Odroid has Xubuntu so it can run XFCE while Rpi can run LXDE (they have a modified version on Raspbian so it runs faster). there are also various more simple windows managers (icewm, jwm) usually available or tiled windows managers (like i3). not sure if they are in their repos or not.

---

### Post by matt_symes on 2015-10-14
Hi

That server is overkill :) 

Nice piece of kit for a small server though and you will be able to hang a WD red or WD purple (for continuous recording).

Are you recording continuously or just when motion is detected ? How much recording is performed in a day ?

What power usage were you looking for ?

BTW I'm going to by an odroid and see how that performs in my quest for a low powered camera system.

Kind regards.

---

