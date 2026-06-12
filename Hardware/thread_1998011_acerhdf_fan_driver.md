---
title: "acerhdf fan driver"
date: 2012-06-06
forum: Hardware
---

### Post by wilsonsamm on 2012-06-06
I have just started using the acerhdf driver to control my fan on my Acer Aspire One ZG5. Previously it was constantly on, draining the battery and making a lot of noise.

Now the behaviour is different, but still not quite right: The fan comes on once every seven seconds or so, and switches off about a second later. Here is my /etc/modprobe.d/acerhdf.conf:
```
options acerhdf interval=10 fanon=75000 fanoff=50000 kernelmode=1
```

Interval is how often it's to check the fan and make the adjustment. 
fanon is how hot the computer should be when the fan comes on,
fanoff is how hot the computer should be when the fan goes off again.
Both temperatures are in thousandths of a degree centigrade.
At the moment, "sensors"  at the command line reports the following temperatures:
```
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +33.0°C  (crit = +90.0°C)                  

acerhdf-virtual-0
Adapter: Virtual device
temp1:       +48.0°C  (crit = +75.0°C)   
```
So what is this strange behaviour?

---

### Post by Onesimus on 2012-06-08
I have exactly the same model as yourself.

I think I have got it working.

What I did was to add the line:
```
acerhdf
```
in /etc/modules.  This loads it during boot.

I also installed jupiter to further increase my battery life.
```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```

Hope this helps

---

### Post by wilsonsamm on 2012-06-08
Thanks for the reply, Onesimus!

I did as you said and added acerhdf to my /etc/modules. Now the fan is off the whole time, none of that stopping/starting business which is good.

But does your fan come on when your computer runs hot? I started transcoding a video, and while monitoring it I found the temperature increased beyond the threshold (75°C) and kept going, but the fan didn't come on. So I stopped the transcoding process and let it cool down a bit.

---

### Post by Onesimus on 2012-06-08
Mine behaves exactly as it should.  I do have my settings in /etc/modprobe.d/acerhdf.conf set to:
```
options acerhdf interval=10 fanon=63000 fanoff=60000 kernelmode=1
```

which is considerably lower temperature than yours.

You can determine whether it is functioning correctly by 
```
dmesg | grep acerhdf
```

It should give just the driver information.

---

### Post by Onesimus on 2012-06-09
What version of Ubuntu are you on ?  I am on 12.04, and if you're not I suggest you move to the latest version.

There is background information on acerhdf at [http://piie.net/files/acerhdf_README.txt]("http://piie.net/files/acerhdf_README.txt")

which may prove helpful.

---

### Post by wilsonsamm on 2012-06-09
> **Onesimus said:**
> What version of Ubuntu are you on ?  I am on 12.04, and if you're not I suggest you move to the latest version.

I was on 10.04 LTS until this morning. I hadn't realised 12.04 had come out! Now I have upgraded to 12.04 and everything is working correctly (and a few other minor issues are gone too!)!

---

