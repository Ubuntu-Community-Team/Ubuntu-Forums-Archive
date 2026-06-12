---
title: "Monitor is not detected in 13.10"
date: 2013-12-17
forum: Hardware
---

### Post by wierdlmate on 2013-12-17
Hello, I hope this is the right forum for this. 

I have a Westinghouse 22 in monitor 

[http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=2929479&pagenumber=1&RSort=1&csid=ITD&recordsPerPage=5&body=REVIEWS&SRCCODE=WEBGOOKWL&cm_mmc_o=mH4CjC7BBTkwCjCs81CjCE&gclid=CJmEzLDRt7sCFcVQ7AoddhwABQ#CustomerReviewsBlock](http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=2929479&pagenumber=1&RSort=1&csid=ITD&recordsPerPage=5&body=REVIEWS&SRCCODE=WEBGOOKWL&cm_mmc_o=mH4CjC7BBTkwCjCs81CjCE&gclid=CJmEzLDRt7sCFcVQ7AoddhwABQ#CustomerReviewsBlock)

and a Gateway SX2800-01 Desktop PC 

[http://reviews.cnet.com/desktops/gateway-sx2800-01/4505-3118_7-33699400.html](http://reviews.cnet.com/desktops/gateway-sx2800-01/4505-3118_7-33699400.html). 

 They are 4 years old. 

According to the above link, the computer has

CPU	2.33GHz Intel Core 2 Quad Q8200	
Memory	4GB 800MHz DDR2 SDRAM	
Graphics	32MB Intel GMA X4500	
	


I get

$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 32767 x 32767
VGA1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)


This is a problem since before my installation of 13.10, I had Ubuntu 13.04 with much higher resolutions than 1024x768 available, and the monitor's highest resolution is 1680x1050. After upgrading to 13.10, the resolution and dbus permissions got messed up making my system unusable, so I decided to install 13.10 fresh.  The problem with screen resolution persists.

Please help to debug and resolve this.

Máté

---

