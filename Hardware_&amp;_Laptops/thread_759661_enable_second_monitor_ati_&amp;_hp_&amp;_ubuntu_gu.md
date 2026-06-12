---
title: "enable second monitor ati &amp; hp &amp; ubuntu gutsy"
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by residentevil on 2008-04-19
Hello, I have a laptop hp Compaq 6715 s and its with ati radeon x 1200 and a want to know ho to enable second monitor via VGA port.

---

### Post by David2926 on 2008-04-19
Do you have the ATI restricted driver installed? Use aticongfig  --initial=check to be sure.  If so use the aticonfig --initial or aticonfig --initial=dual-head. Also aticonfig --help will give all the options. Note I have problems with the Ubuntu driver manager and ATI cards, so I go to the ATI site and download the required driver. Be sure to get the Xpress 1200 IGP driver not the standard radeon X1200 driver.
Warning - I have run dual monitors on desktops for years, but not on laptops, so switching from dual-head to single may cause problems. Remember aticonfig --initial.
Good luck David

---

