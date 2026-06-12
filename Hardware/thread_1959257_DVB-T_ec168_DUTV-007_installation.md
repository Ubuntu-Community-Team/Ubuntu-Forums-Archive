---
title: "DVB-T ec168 DUTV-007 installation"
date: 2012-04-15
forum: Hardware
---

### Post by gunner814 on 2012-04-15
Hello all
I am trying to install my DVB-T dongle on Ubuntu 11.10. this is my lsusb result

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 18b4:1001 e3C Technologies DUTV007

I have copied dvb-usb-ec168.fw fo /lib/firmware and installed mercurial however when I run 
hg clone [http://linuxtv.org/hg/~anttip/ec168/](http://linuxtv.org/hg/~anttip/ec168/) I get the following results

abort: 'http://linuxtv.org/hg/~anttip/ec168/' does not appear to be an hg repository:
---%<--- (text/html; charset=UTF-8)
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en-US">
<head>
<link rel="icon" href="/hg/static/hgicon.png" type="image/png" />
<meta name="robots" content="index, nofollow" />
<link rel="stylesheet" href="/hg/static/style-paper.css" type="text/css" />

<title>Mercurial repositories index</title>
</head>
<body>

<div class="container">
<div class="menu">
<a href="http://mercurial.selenic.com/">
<img src="/hg/static/hglogo.png" width=75 height=90 border=0 alt="mercurial" /></a>
</div>
<div class="main">
<h2>Mercurial Repositories</h2>

<table class="bigtable">
    <tr>
        <th><a href="?sort=name">Name</a></th>
        <th><a href="?sort=description">Description</a></th>
        <th><a href="?sort=contact">Contact</a></th>
        <th><a href="?sort=lastchange">Last modified</a></th>
        <th>&nbsp;</th>
    </tr>
    
<tr class="parity0">
<td><a href="/hg/~anttip/ec168/suspend/">suspend</a></td>
<td>suspend development repository</td>
<td>&#65;&#110;&#116;&#116;&#105; &#80;&#97;&#108;&#111;&#115;&#97;&#97;&#114;&#105;</td>
<td class="age">2009-09-20</td>
<td class="indexlinks"><a href="/hg/~anttip/ec168/suspend/archive/tip.zip">&nbsp;&darr;zip</a><a href="/hg/~anttip/ec168/suspend/archive/tip.tar.gz">&nbsp;&darr;gz</a><a href="/hg/~anttip/ec168/suspend/archive/tip.tar.bz2">&nbsp;&darr;bz2</a></td>
</tr>

<tr class="parity1">
<td><a href="/hg/~anttip/ec168/rtl2831u/">rtl2831u</a></td>
<td>rtl2831u development repository</td>
<td>&#65;&#110;&#116;&#116;&#105; &#80;&#97;&#108;&#111;&#115;&#97;&#97;&#114;&#105;</td>
<td class="age">23 months ago</td>
<td class="indexlinks"><a href="/hg/~anttip/ec168/rtl2831u/archive/tip.zip">&nbsp;&darr;zip</a><a href="/hg/~anttip/ec168/rtl2831u/archive/tip.tar.gz">&nbsp;&darr;gz</a><a href="/hg/~anttip/ec168/rtl2831u/archive/tip.tar.bz2">&nbsp;&darr;bz2</a></td>
</tr>

<tr class="parity0">
<td><a href="/hg/~anttip/ec168/rtl2831u_4/">rtl2831u_4</a></td>
<td>rtl2831u development repository</td>
<td>&#65;&#110;&#116;&#116;&#105; &#80;&#97;&#108;&#111;&#115;&#97;&#97;&#114;&#105;</td>
<td class="age">2009-08-26</td>
<td class="indexlinks"><a href="/hg/~anttip/ec168/rtl2831u_4/archive/tip.zip">&nbsp;&darr;zip</a><a href="/hg/~anttip/ec168/rtl2831u_4/archive/tip.tar.gz">&nbsp;&darr;gz</a><a href="/hg/~anttip/ec168/rtl2831u_4/archive/tip.tar.bz2">&nbsp;&darr;bz2</a></td>
</tr>

<tr class="parity1">
<td><a href="/hg/~anttip/ec168/qt1010/">qt1010</a></td>
<td>qt1010 development repository</td>
<td>&#65;&#110;&#116;&#116;&#105; &#80;&#97;&#108;&#111;&#115;&#97;&#97;&#114;&#105;</td>
<td class="age">2010-01-12</td>
<td class="indexlinks"><a href="/hg/~anttip/ec168/qt1010/archive/tip.zip">&nbsp;&darr;zip</a><a href="/hg/~anttip/ec168/qt1010/archive/tip.tar.gz">&nbsp;&darr;gz</a><a href="/hg/~anttip/ec168/qt1010/archive/tip.tar.bz2">&nbsp;&darr;bz2</a></td>
</tr>

<tr class="parity0">
<td><a href="/hg/~anttip/ec168/rtl2831u_qt1010/">rtl2831u_qt1010</a></td>
<td>rtl2831u_qt1010 development repository</td>
<td>&#65;&#110;&#116;&#116;&#105; &#80;&#97;&#108;&#111;&#115;&#97;&#97;&#114;&#105;</td>
<td class="age">2010-02-16</td>
<td class="indexlinks"><a href="/hg/~anttip/ec168/rtl2831u_qt1010/archive/tip.zip">&nbsp;&darr;zip</a><a href="/hg/~anttip/ec168/rtl2831u_qt1010/archive/tip.tar.gz">&nbsp;&darr;gz</a><a href="/hg/~anttip/ec168/rtl2831u_qt1010/archive/tip.tar.bz2">&nbsp;&darr;bz2</a></td>
</tr>

<tr class="parity1">
<td><a href="/hg/~anttip/ec168/rtl2831u_3/">rtl2831u_3</a></td>
<td>unknown</td>
<td>&#117;&#110;&#107;&#110;&#111;&#119;&#110;</td>
<td class="age">2009-08-25</td>
<td class="indexlinks"><a href="/hg/~anttip/ec168/rtl2831u_3/archive/tip.zip">&nbsp;&darr;zip</a><a href="/hg/~anttip/ec168/rtl2831u_3/archive/tip.tar.gz">&nbsp;&darr;gz</a><a href="/hg/~anttip/ec168/rtl2831u_3/archive/tip.tar.bz2">&nbsp;&darr;bz2</a></td>
</tr>

</table>
</div>
</div>


</body>
</html>


---%<---
!
I am now at a bit of a`loss as to the next step any help would be appreciated

Thanks

Adam

---

### Post by StephanVolkmann on 2012-06-25
the repo is down for 1-2 years because driver are included nativ in newer kernels....

---

