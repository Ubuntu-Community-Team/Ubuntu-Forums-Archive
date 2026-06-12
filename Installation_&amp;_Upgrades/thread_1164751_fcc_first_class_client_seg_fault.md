---
title: "fcc first class client seg fault"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by funsnail on 2009-05-19
I had a problem with first class today. It would show the login but not connect. When I ran it under a terminal it showed a seg fault. I solved the problem by using aptitude to check fcc for dependencies. When I followed the libqt3-mt dependency and checked it's dependencies I found 3 libraries under Suggests that weren't installed. The libraries were libqt3-mt-mysql, libqt3-mt-odbc, and libqt3-mt-psql. I marked them for install. Some of them had more dependencies and updated. After the installations first class runs with no seg faults.

I am running Ubuntu 9.04 upgraded from 8.10 on i386 and fcc 9.124 installed from the deb package.

Hope this information helps someone else facing a similar situation.

---

### Post by funsnail on 2009-05-20
Never mind.. It stopped working and I am ready to pull my hair out. It works fine on my laptop with a fresh install of Ubuntu 9.04

---

### Post by funsnail on 2009-05-21
Well I broke down today and reinstalled 9.04. I now have first class running with no problems.

---

