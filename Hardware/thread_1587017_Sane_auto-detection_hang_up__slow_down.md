---
title: "Sane auto-detection hang up / slow down"
date: 2010-10-02
forum: Hardware
---

### Post by farside268 on 2010-10-02
I am using a Canon MX850 multifunction on a Ubuntu 10 machine. I am able to connect the the scanner via ethernet, but there is a considerable delay every time I try to access the scanner because the sane.d backend insists on searching my local network for scanners. The debug output shows that the scanner is found, but the backend keeps searching for additional scanners. It finds the original scanner four more times and properly identifies them as already having been found.

Is there any way to disable the auto detection feature or keep the backend from re-detecting repeatedly?

As it is, I usually have to wait 1-2 minutes for this process to be completed each time I try to access my scanner.

Any suggestions?

---

### Post by IcarusR on 2010-10-03
You could try defining your scanner in /etc/sane.d/pixma.conf have alook at the backend man page.

[http://www.sane-project.org/man/sane-pixma.5.html]("http://www.sane-project.org/man/sane-pixma.5.html")

---

### Post by farside268 on 2010-10-04
> **IcarusR said:**
> You could try defining your scanner in /etc/sane.d/pixma.conf have alook at the backend man page.

[http://www.sane-project.org/man/sane-pixma.5.html](http://www.sane-project.org/man/sane-pixma.5.html)

I had already done that. The debug output shows that the pixma backend configures the manually configured scanner first but then continues to auto detect it four times.

---

### Post by andrew_peru on 2011-01-19
I know it's been a while since this post, but since I banged my head against the wall  for 3 days with the same problem (slow auto-detect on a networked PIXMA 860) and I finally found a solution that worked (in my case: Jaunty with sane 1.0.22 built from source) I figured I'd share the solution, in case it helps anybody.

Short answer:     
Your PIXMA needs to be referenced with a static IP in the /etc/hosts file.

How: 
               sudo vi /etc/hosts            
or         
sudo <my favorite editor> /etc/hosts

then add a line like:     

192.168.100.45    my_scanner_printer

where "192.168.100.45" should be replaced by the real IP address of your device
and  "my_scanner_printer" can be any arbitrary name that you want to assign to your device.

In my case I made sure that my PIXMA 860 had a static IP address by setting it in the DHCP server of my router, it may be possible to do this directly on the device but I never found (not that I looked that hard) documentation explaining how to do this.

I found the solution by monitoring network traffic with wireshark and realizing that when I ran "scanimage -L" my computer would make a lot of reverse DNS requests to my router wanting to know who "192.168.100.45" was.  I googled around and found that a solution often suggested for complaints of excessive reverse DNS requests is to include entries for "unknown" devices in one's /etc/hosts file.

An alternative solution might be using an internal DNS or DDNS server to name the device.

---

### Post by hayhursm on 2011-02-27
> **andrew_peru said:**
> I know it's been a while since this post, but since I banged my head against the wall  for 3 days with the same problem (slow auto-detect on a networked PIXMA 860) and I finally found a solution that worked (in my case: Jaunty with sane 1.0.22 built from source) I figured I'd share the solution, in case it helps anybody.

Short answer:     
Your PIXMA needs to be referenced with a static IP in the /etc/hosts file.

How: 
               sudo vi /etc/hosts            
or         
sudo <my favorite editor> /etc/hosts

then add a line like:     

192.168.100.45    my_scanner_printer

where "192.168.100.45" should be replaced by the real IP address of your device
and  "my_scanner_printer" can be any arbitrary name that you want to assign to your device.

In my case I made sure that my PIXMA 860 had a static IP address by setting it in the DHCP server of my router, it may be possible to do this directly on the device but I never found (not that I looked that hard) documentation explaining how to do this.

I found the solution by monitoring network traffic with wireshark and realizing that when I ran "scanimage -L" my computer would make a lot of reverse DNS requests to my router wanting to know who "192.168.100.45" was.  I googled around and found that a solution often suggested for complaints of excessive reverse DNS requests is to include entries for "unknown" devices in one's /etc/hosts file.

An alternative solution might be using an internal DNS or DDNS server to name the device.


Sir, you are a genius!!  I have been frustrated for months because there was a long delay between the time I opened XSANE until my networked Pixma MX860 was detected and I just dealt with it.  I searched everywhere on the the web and tried changing different SANE config files to speed up the detection process but absolutely nothing would work...until I came across your post.  Using Wireshark to see what actually is happening behind the scenes was a brilliant idea!!!  I guess I still have a lot to learn.  I never thought it would be something as simple as the hosts file.   Thank you!!  =D>

---

