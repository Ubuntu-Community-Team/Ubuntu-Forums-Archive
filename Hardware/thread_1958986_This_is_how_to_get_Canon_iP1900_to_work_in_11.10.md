---
title: "This is how to get Canon iP1900 to work in 11.10"
date: 2012-04-15
forum: Hardware
---

### Post by fauzie on 2012-04-15
I've been using my printer since the first time I use ubuntu, and it always work flawlessly, until I upgraded my system to 11.10, and voila my printer stops working. Because I've spent quite a lot of time figuring out how to get arround this issue, I think it is worth to share the steps here.

So this is what initially happened:

I installed the new ubuntu on a fresh hard disk. All hardwares work without problem. I turned on my printer, and ubuntu detects it correctly, and install the driver automagically. Then I proceeded to print the test page. The status monitor showed the progress going to about 25%, the printer lamp is blinking as it receives the data, but it doesn't print out anything. At the end the status monitor says the printer is idle. Nothing is ever printed.

The next step is off course google, which guided me to this page
[http://www.upubuntu.com/2011/10/how-to-install-canon-pixma-ip1800.html]("http://www.upubuntu.com/2011/10/how-to-install-canon-pixma-ip1800.html")
You may want to try your luck there. It worked for me, but in the downside, I noticed no matter which setting that I chose, the printer will send the same thing. This might be enough for most people, but I would like to do more. It worked before anyway.

So I tried to install the official driver from the canon website, which is off course very old and broken as any other manufacturer's linux driver. but apparently the deb package is broken simply because at one point, the ubuntu developers changed libcupsys2 to libcups2.

If you want to do it the dirty way, you can follow this post
[http://ubuntuforums.org/archive/index.php/t-1305248.html]("http://ubuntuforums.org/archive/index.php/t-1305248.html")

But if you scroll to the bottom of the page somebody made the modified debian that will install very well on a 11.10 system, which is available here:
[https://skydrive.live.com/?cid=3f4cf8fc74f13a9a&id=3F4CF8FC74F13A9A%21489]("https://skydrive.live.com/?cid=3f4cf8fc74f13a9a&id=3F4CF8FC74F13A9A%21489")

So go ahead and download the file above. Turn off your printer, open the Software Center and remove the installed cnijfilter package (common and the iP1900). Then unzip the downloaded file, and install both deb packages.

Turn on the printer, and it will detect and install the printer with the new (old?) driver. Try to print something out, if you're lucky, it may work right away, but in my case, I got an "insecure filter" problem. Click on Diagnose at the error message pop up windows, and it will show you the problematic file. In my case I just have to type in

```
sudo chown root /usr/lib/cups/filter/pstocanonij
```

note: the error is caused by the filter is not owned by root. 

In my case, my printer worked at this point. There will be no setting available, but they can be made available by editing

/usr/share/cups/model/canonip1900.ppd

and adding these lines

```
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality
```

find also these lines 
```
 *OpenUI *Resolution/Output Resolution: PickOne

*DefaultResolution: 600

*Resolution 600/600 dpi: "<>setpagedevice"

*CloseUI: *Resolution 
```

and change them with

```

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*Resolution 4800/4800 dpi: "<</HWResolution[4800 4800]>>setpagedevice"
*CloseUI: *Resolution

```

At this point you should by able to change the setting by 
- access CUPS with a web browser at [http://localhost:631](http://localhost:631)
- click on Printers tab
- choose the printer iP1900-series
- Administration -> Modify printer
- Click continue twice
- When prompted "Or Provide a PPD File", point the the /usr/share/cups/model/canonip1900.ppd
- Click on Modify Printer

The setting is done at this point. To change the setting, again click on Printers tab, choose the printer, then Administration -> Set Default Options.

Good luck. I wish somebody can provide a clearer, easier, shorter solution to this problem :lolflag:

---

