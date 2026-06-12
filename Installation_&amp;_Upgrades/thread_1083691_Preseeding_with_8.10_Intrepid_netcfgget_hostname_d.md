---
title: "Preseeding with 8.10 Intrepid netcfg/get_hostname doens't work."
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by trekkie3k on 2009-03-01
Hi,

I'm trying to do a completely automated installation of intrepid. (Using the alternate install image (amd64). (Would it even work with the standard desktop image?)

I've been trying to get rid of a specific problem all day now. But from all examples I've found and everything I've tried I think I miss something or there is a bug. I can't get past the hostname dialog.

What I do so far:

I set the following option using kernel options:
```
locale=en_GB kbd-chooser/method=de DEBCONF_DEBUG=5 url=http://installserver.ing3.dnet/ubuntu0810/./preseed
```

With that I get language and keyboard set, Network information is automatically set up using DHCP. After DHCP I get the hostname dialog preset with the hostname given by DHCP. As far as I understand it if DHCP gives a hostname this dialog shouldn't appear at all.

In my preseed file I tried all sorts of options that were used in other examples on the net (alone, in combination, whatever ...):
```
d-i netcfg/choose_interface select auto
d-i netcfg/disable_dhcp boolean false
d-i netcfg/dhcp_hostname string
d-i netcfg/dhcp_hostname seen true
d-i netcfg/get_hostname string
d-i netcfg/get_hostname seen true
```

But all that doesn't get me past the hostname dialog. It seems to me that the options are not respected or I missed something.

...

I can get behind the dialog, setting debconf/priority to critical (get_hostname=high), but not if it is set in the preseed file. I don't really like setting to much options with kernel parameters ...

I'd be glad to hear any suggestions.

Thanks everyone :)

---

