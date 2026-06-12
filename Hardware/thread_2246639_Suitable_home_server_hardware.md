---
title: "Suitable home server hardware"
date: 2014-10-02
forum: Hardware
---

### Post by anthony40 on 2014-10-02
I am currently running a 9.10 karmic server which host a file server, mail server, web mail server  vpn and nat gateway + firewall.

Current load:
4 mail users
2 file share users
1 VPN user

I am looking to upgrade this server software,  but I am thinking perhaps to replace the hardware as well. Current hardware is more than 10 years old.

I am thinking to replace the NAT-gateway and firewall by a router so the requirements are as follows:

1 Ethernet port
Minimum 1 TB disk
2-4 usb ports
Ideally  low wattage,  
Silent alternatives preferable

I am looking to upgrade to one of the latest LTS versions.

Any suggestions on what to buy?  I am thinking about something like the Apple Mini but cheaper PC alternatives.

Thanks

---

### Post by TheFu on 2014-10-02
For that load, any dual core Atom clone will be sufficient. Something in the 16W range should be fine.  That means you can get a picoPSU, which will be completely silent. 1G of RAM should be fine, unless you go crazy on the storage and use ZFS - then 8G is the minimal and more is better.

Running 9.10 on any network is really dangerous. I'd be surprised if it wasn't already hacked. It hasn't been supported in about 4 yrs. Please, stay with LTS releases going forward for longer support periods and don't wait until after support ends to migrated to the next LTS release. It is nearly impossible to get any help on those older releases now and I suspect this thread will be moved somewhere else (discussion of unsupported releases isn't allowed in normal forums).

BTW - just saw a "shell shocker" build for $199 on slickdeals/bensbargains through newegg. That would be overkill for your needs, but is new hardware needed at all?  The CPU in that deal is over 50W alone, but it does include everything except the OS.

---

### Post by mörgæs on 2014-10-02
Agree on the advice about installing a supported release.

A server install can run on very modest hardware, also more than ten years old. Why do you want to change hardware - do you see performance problems running **top**, for example?

---

### Post by anthony40 on 2014-10-06
Hi,

Thanks for the advice, I have not been hacked as  far as I can tell but a reinstall on a new system will certainly solve that. 

Regarding the hardware:

I am mostly concerned about the power unit which is old and probably not replacable (weird chassis). And its way to big for its purpose, so its not that the cpu or memory can't take it.

Do you have any links to where these are sold?  I would prefer buying a out of the box machine,  I don't want to put the time and effort into building a machine myself.

---

### Post by Michael_McKenney on 2014-10-06
My only question will be your ISP allowing it.  My ISP will turn off my connection if it detects SMTP or certain server traffic.  You might want to see what they will allow before buying hardware.

---

### Post by ian-weisser on 2014-10-06
I agree with offloading gateway and LAN firewall to a router. I found it makes connectivity more reliable; crashed server services don't kill the network.

I agree with TheFu on hardware. Lots of low-end low-power hardware will run 14.04 Server just fine. Mail and VPN are not CPU-intensive.

My current home server (using 14.04 Server) runs on a 9-year old low-end laptop with closed lid next to the router.

---

### Post by mastablasta on 2014-10-07
> **TheFu said:**
> 
BTW - just saw a "shell shocker" build for $199 on slickdeals/bensbargains through newegg. That would be overkill for your needs, but is new hardware needed at all?  The CPU in that deal is over 50W alone, but it does include everything except the OS.

care to share a link? I am interested though I already bought it. I am more interested at what 200USD gets you in terms of home server PC.

---

