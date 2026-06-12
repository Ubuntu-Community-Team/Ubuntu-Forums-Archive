---
title: "dsl not working after bool"
date: 2008-08-26
forum: General Help
---

### Post by froebi on 2008-08-26
Hi,

since a few days my dls connection is not working after booting by Hardy Kubuntu box. When restarting netwoking with 'sudo /etc/init.d/networking restart' everything works fine. So my guess was that networking was somehow not started on boot. I had a look at 'System Settings->System Services' and indeed networking was not listed to be started at boot.

Anyone any idea what this is all about?

I then tried to work around the problem by simply checking the 'Start at Boot' flag in 'System Services' (for runlevel 2). But still it doesn't work.

I then tried to tinker with update-rc.d but things got worse then. I think some services' boot dependencies are mixed up now. But I'm not sure as my knowledge of init (or upstart now?) is not the best. One thing I noticed in the /etc/init.d/networking script is that the header's 'default start'-entries looked quite strange:
# Default-Start:     S
# Default-Stop:      0 6

Is that supposed to be correct?

Last question: Is there any way to get the defaults back to /etc/rc*.d?

regards,
  Christian

---

### Post by froebi on 2008-08-27
Well, I think I finally found out myself what all this was about. Recently I wanted to test an USB-WLAN-adapter. For this, I somehow installed the network-manager package. I guess this was the root cause of my problems.

First, it removed the networking service from runlevel 2
Second, it takes control of /etc/resolv.conf

This at least explains my observations: Even after I manually pulled back the networking service into runlevel 2, the dsl-connection did not work after boot although the dsl-connection had been established during boot (as seen in the logs). Usually, pppd changed /etc/resolv.conf. Maybe it still did. But later in the boot process network-manager did override this changes.

After deinstalling network-manager, everything works fine again.

I was just wondering that if network-manager and dsl-connections and the like don't work well together, maybe this install script (or whatever) should check for incompatibilities and at least warn the user.

I also had a look at network-manager's home page. There it says "Pain-free networking". -- Well, not for me this time:(

Christian

---

