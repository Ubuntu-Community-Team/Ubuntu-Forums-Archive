---
title: "Monitor Flicker problems"
date: 2009-06-22
forum: Hardware
---

### Post by doublemike on 2009-06-22
I'm running 9.04 on a Toshiba Satellite and have a problem with screen flicker. It is especially bad if I'm running firefox with a page that has a JavaScript slide show or other effect that updates using a fade effect. I've also see it with streaming video and when other apps besides firefox are running.

I'm thinking it is related to the graphics card and driver. I did a check and it looks like I have the ATI.

$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]

Would  switching from the proprietary fglr driver to the Radeon driver ( [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) ) fix this problem?

Thanks,
Mike

PS. Problem is relate to the whole ATI graphics card driver mess.

---

