---
title: "Pidgin RVP will not connect in Hardy"
date: 2008-08-22
forum: General Help
---

### Post by Coreigh on 2008-08-22
I have been using Pidgin and the RVP plugin for MS Exchange on Gutsy for over a year. I want to upgrade to Hardy but Pidgin and RVP will not work. I have un-installed and deleted the .purple directory and re-installed several times. And I tried the pre-built packages and compiling from source. I always get the same error: "server returned empty response to SUBSCRIBE request" and the account is disabled. I am _still able_ to connect and use Pidgin on another computer running Gutsy. I am beginning to suspect the problem may not be Pidgin or the RVP plugin but some other config. in Hardy. Does anyone have any ideas? The debug data is posted below.


```
(16:57:18) account: Connecting to account utegaact
(16:57:18) connection: Connecting. gc = 0x8511b28
(16:57:18) rvp_login: Enter
(16:57:18) rvp_login: No srv record, falling back on omnent
(16:57:18) rvp_login: Allocated 0x8511b60 for rd->principal
(16:57:18) rvp_login: Connecting to omnent:80
(16:57:18) prefs: purple_prefs_get_bool: Unknown pref /core/network/ports_range_use
(16:57:18) dns: DNS query for 'omnent' queued
(16:57:18) dns: Created new DNS child 1295, there are now 1 children.
(16:57:18) dns: Successfully sent DNS request to child 1295
(16:57:18) dns: Got response for 'omnent'
(16:57:18) dnsquery: IP resolved for omnent
(16:57:18) proxy: Attempting connection to 172.16.6.6
(16:57:18) proxy: Connecting to omnent:80 with no proxy
(16:57:18) proxy: Connection in progress
(16:57:18) proxy: Connected to omnent:80.
(16:57:18) rvp_login_connect: enter
(16:57:18) network: Listening on port: 48401
(16:57:18) rvp_login_connect: exit
(16:57:19) network: Couldn't create UPnP mapping
(16:57:19) network: Couldn't create UPnP mapping
(16:57:19) rvp_main_listener_callback: listening on port 48401, fd 6
(16:57:19) rvp_main_listener_callback: listener hookup
(16:57:19) rvp_get_sessid: generated new ID 72D288EB-CFE3-40FA-6E3B-DC904B9753F9
(16:57:19) rvp_build_request: allocated header 0x8505688 for SUBSCRIBE http://omnent/instmsg/aliases/utegaact
(16:57:19) dns: DNS query for 'omnent' queued
(16:57:19) rvp_main_listener_callback: exit
(16:57:19) dns: Created new DNS child 1297, there are now 1 children.
(16:57:19) dns: Successfully sent DNS request to child 1297
(16:57:19) dns: Got response for 'omnent'
(16:57:19) dnsquery: IP resolved for omnent
(16:57:19) proxy: Attempting connection to 172.16.6.6
(16:57:19) proxy: Connecting to omnent:80 with no proxy
(16:57:19) proxy: Connection in progress
(16:57:19) proxy: Connected to omnent:80.
(16:57:19) url_fetched_cb_cond: Requesting 0x8502fb8:
SUBSCRIBE /instmsg/aliases/utegaact HTTP/1.1
Content-Length: 0
RVP-Notifications-Version: 0.2
Host: omnent
Notification-Type: pragma/notify
RVP-From-Principal: http://omnent/instmsg/aliases/utegaact
Subscription-Lifetime: 14000
Call-Back: http://172.16.6.148:48401


(16:57:19) url_fetched_cb_cond: inserting 0x8502fb8 into pending list
(16:57:23) util: Writing file accounts.xml to directory /home/utegaact/.purple
(16:57:23) util: Writing file /home/utegaact/.purple/accounts.xml
(16:57:49) rvp_request_timeout: 0x8502fb8 timed out
(16:57:49) rvp_async_data: callback on gfud 0x8502fb8
(16:57:49) account: Disconnecting account 0x814d290
(16:57:49) connection: Disconnecting connection 0x8511b28
(16:57:49) rvp_close: enter
(16:57:49) rvp_close: apparently I'm not logged in
(16:57:49) rvp_close: freeing 0x8511b60 principal
(16:57:49) rvp_close: exit
(16:57:49) connection: Destroying connection 0x8511b28
(16:57:54) util: Writing file accounts.xml to directory /home/utegaact/.purple
(16:57:54) util: Writing file /home/utegaact/.purple/accounts.xml
(16:58:48) rvp_async_data: callback on gfud 0x8502fb8
(16:58:48) rvp_async_data: Woah, rvpdata is null!
(16:58:48) url_fetched_cb_cond: closing socket for 0x8502fb8
(16:58:48) destroy_fetch_url_data: Enter 0x8502fb8
(16:58:48) destroy_fetch_url_data: freeing header 0x8505688
(16:58:48) destroy_fetch_url_data: removing 0x8502fb8 from pending list
(16:58:48) destroy_fetch_url_data: Exit

```

---

### Post by Grendelmon on 2008-09-24
Yup, I have the same problem running Xubuntu Hardy.

---

### Post by thaibox1 on 2009-01-21
I'm having the same issue with Intrepid.  Has anyone figured out why this is happening?  Should we submit a bug in launchpad?

Thanks.

---

### Post by thaibox1 on 2009-04-23
Not sure if anyone has seen this, but I found a patch that someone else created to fix this issue (at least it worked for me).  Apply the patch from [http://anil.net.in/files/misc/rvp.c.patch](http://anil.net.in/files/misc/rvp.c.patch) against librvp-0.9.7 as downloaded from [http://www.waider.ie/hacks/workshop/c/rvp/](http://www.waider.ie/hacks/workshop/c/rvp/)

I had to remove the ubuntu pidgin-librvp package and then compile my own using the above patch.  A simple configure; make; sudo make install worked like a charm.

Hope this helps.

EDIT: The above patch only helps you SEND messages, I still can't receive any, so I'm still at square one.  Although, I have seemingly stumbled upon the issue by looking at wireshark.  It seems that our corp Exchange Messaging Service sits behind a load balancer and it seems that librvp is stumbling on the redirect from the load balancer.  However, configuring to go direct to a specific server doesn't work either.

---

