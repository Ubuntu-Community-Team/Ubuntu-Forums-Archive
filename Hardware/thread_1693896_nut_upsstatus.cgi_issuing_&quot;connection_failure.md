---
title: "nut upsstatus.cgi issuing &quot;connection failure: connection refused&quot; messages"
date: 2011-02-23
forum: Hardware
---

### Post by Suncat2000 on 2011-02-23
I configured [FONT="Courier New"]nut[/FONT] to monitor my UPS and control my workstation's shutdown. After I got it working, I installed the [FONT="Courier New"]**nut-cgi**[/FONT] package for a nicer interface to check on the status of the UPS. My [FONT="Courier New"]nut[/FONT] configuration was set up and working properly already. I added the information to [FONT="Courier New"]hosts.conf[/FONT] so the CGI program would return the monitoring data.

When I fired up the script through my web browser, it was able to list the UPS, but where the data was supposed to be, I just got the message:

```
[COLOR="Red"]Connection failure: connection refused.[/COLOR]
```

My [FONT="Courier New"]hosts.conf[/FONT] file contains:
```
MONITOR smart-ups@myserver "smart-ups: APC Smart-UPS 1100XL on MyServer"
```

Here's what I get as a status page:

```
Network UPS Tools upsstats 2.4.3
Wed Feb 23 14:06:39 EST 2011
System 	Model 	Status 	Battery 	Input (VAC) 	Output (VAC) 	Load (%) 	UPS
Temp 	Battery
Runtime 	Data
Tree
smart-ups: APC Smart-UPS 1100XL on MyServer 	[error: Connection failure: Connection refused] 	[error: Connection failure: Connection refused] 							All data

```

I verified that [FONT="Courier New"]upsd[/FONT] was running and responding correctly.

Can somebody tell me how to fix this so I can use the CGI script to display my UPS status?

---

### Post by Suncat2000 on 2011-02-23
After hours of pointless web searching, including the Ubuntu forums, I came up empty. But reading posts about [FONT=Courier New]nut[/FONT]-related problems gave me the idea of reviewing my configuration files and trying various changes.

The solution, it turns out, has to do with the network security implemented by [FONT=Courier New]nut[/FONT] itself. In my [FONT=Courier New]/etc/nut/hosts.conf[/FONT] file, I added the entry "smart-ups@myserver", which is the UPS on my server named "myserver". [FONT=Courier New]upsmon[/FONT], [FONT=Courier New]upsd[/FONT], and my web server running [FONT=Courier New]upsstats.cgi[/FONT], are all on the same machine.

I was running nut in Standalone mode and had nothing customized in [FONT=Courier New]upsd.conf[/FONT], so [FONT=Courier New]upsd[/FONT] was binding to the default port, as if the following entry were there:
```
LISTEN 127.0.0.1 3493
```The result was that [FONT=Courier New]upsd[/FONT] binds to a *specific network interface*, in this case **127.0.0.1** (that is, localhost), or the loopback interface, **lo**. Because I specified the server name in [FONT=Courier New]hosts.conf[/FONT], [FONT=Courier New]upsstats.cgi[/FONT] was attempting to access upsd at address **192.168.1.5**, which is my Ethernet interface, **eth1**, on myserver.

The fix was to modify [FONT=Courier New]hosts.conf[/FONT] from "smart-ups@myserver" to "smart-ups@localhost" to direct [FONT=Courier New]upsstats.cgi[/FONT] to use the correct interface.

Now it works and I have my nice UPS status display.

---

