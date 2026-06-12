---
title: "D Link DSL 504T ADSL Router"
date: 2005-01-17
forum: Hardware &amp; Laptops
---

### Post by arh4108 on 2005-01-17
I have managed to rig up and connect a pppoA connection and also ping a website successfully.  I believe I have a DNS / Ethernet problem as on transmission there are carrier sense errors and no successful transmissions. This results in Firefox being unable to display web pages even though the system is showing connected to the internet.

Any thoughts would be most welcome...

---

### Post by python on 2005-01-17
Go to COMPUTER--->SYSTEM CONFIGURATION--->NETWORKING (you will need to be superuser (root))

Then go to the DNS tab (probably 192.168.blah.blah as entry)

Find out your ISPs DNS nameservers, for example, Tiscali is 212.74.112.66 and 212.74.112.67.

Enter those bad boys in. Take 192.168.blah.blah OUT!



Then go to /etc/resolv.conf
Make sure that these two entries are there:

[COLOR=Red]nameserver 212.74.112.66
nameserver 212.74.112.67[/COLOR]

Your ISPs nameservers replacing mine ;-P
Nameserver 192.168.blah.blah should either be commented out (preceded with a #) or not be there at all.



Finally, go to /etc/dhcp3/dhclient-script and comment out this:

[COLOR=Red]# Modified for Debian.  Matt Zimmerman and Eloy Paris, December 2003

# The alias handling in here probably still sucks. -mdz

#make_resolv_conf() {
#    if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
#        local new_resolv_conf=/etc/resolv.conf.dhclient-new
#        rm -f $new_resolv_conf
#
#        if [ -n "$new_domain_name" ]; then
#            echo search $new_domain_name >> $new_resolv_conf
#        else # keep 'old' search/domain scope
#            egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> \
#                  $new_resolv_conf
#        fi
#        
#        if [ -n "$new_domain_name_servers" ]; then
#            for nameserver in $new_domain_name_servers; do
#                echo nameserver $nameserver >>$new_resolv_conf
#            done
#        else # keep 'old' nameservers
#            egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
#                  $new_resolv_conf
#        fi
#
#        chown --reference=/etc/resolv.conf $new_resolv_conf
#        chmod --reference=/etc/resolv.conf $new_resolv_conf
#        mv $new_resolv_conf /etc/resolv.conf
#    fi
#}[/COLOR]


That should have you sorted sunshine!

---

### Post by arh4108 on 2005-01-18
Python -Thanks for the info. 

I am new to Linux and have a lot to learn. I will follow your suggestions. I also happen to use Tiscali so your numbers should work for me.

---

### Post by arh4108 on 2005-01-19
Woohoo It works... :smile: 

I have also learnt how to use Gedit as a superuser and a bit about Nautilus in following your instructions. 

I would never have worked out that I needed to edit dhclient-script by myself - Python - How did you gain your knowledge and can anyone suggest the best way of increasing Ubuntu knowledge other than of course reading these forums :smile: 

Thanks Again

---

### Post by python on 2005-01-19
[QUOTE=arh4108]Woohoo It works... :smile: 

I have also learnt how to use Gedit as a superuser and a bit about Nautilus in following your instructions. 

I would never have worked out that I needed to edit dhclient-script by myself - Python - How did you gain your knowledge and can anyone suggest the best way of increasing Ubuntu knowledge other than of course reading these forums :smile: 

Thanks Again[/QUOTE]
 Glad it's all sorted out. Just playing with Linux all the time really. Reading forums. Programming a little bit of python :-) LInux tutorials as well. Just take an interest and you pick stuff up.

---

### Post by Geoffers on 2005-01-30
Thanks Python!

I'm a Linux newby and have been having the same problem with my D-Link 604T.
Now it all works fine!

Thank you.

Geoff

---

### Post by olieviya on 2005-12-11
[QUOTE=python](you will need to be superuser (root))
[/QUOTE]


How do I become superuser? How do I know if I am?

---

### Post by handy on 2005-12-17
Python,

You probably never look back.  :) 

I had not been able to access the repository's since installation of Breezy on my 64 bit machine. (4 days)

Couldn't even access the internet untill I turned off IPv6 in Firefox through using "about:config".

Searching wiki's, scanning the forum high & low, & then I foung your post here, complex & simple to execute.

Beautiful solution, I thank you.  :KS 

I have voted excellent & sugested to ubuntu_demon that this solution gets somehow sticky, it could help a lot of others save a lot of time & stress.

**[EDIT:]**  My Modem/Router is a Netgear DG-632      ISP -  Telstra Australia :-(

Cheers,

handy

---

### Post by python on 2005-12-17
glad to help :smile:

---

### Post by Pretzal on 2005-12-25
Python - you are a legend. I've recently bought a D-Link G604T Router and have followed your suggestions and it works. Thank you so much. People like you make Ubuntu so worthwhile. :D :D :D

---

### Post by oliwally on 2006-01-17
Bonza rip-snorting-beauty ! After 5 hours of trying other things, this one worked. I have no idea how or why, but it worked. Well done python and thanks!

---

### Post by shankar96 on 2006-02-12
Hello..
  This was the best post I ever found since 2 days, and it worked like magic !!!!! Just too good!!! Deserves a 5/5 rating !! I voted already.. :D Thanks a ton.....
  By the way, I use a DSL-502T..

---

### Post by ema++ on 2006-02-19
Thanks. One day of working, one day without success.
One minute in this forum and...voilà, my router works perfectly and I can 
go in the WEB.

Followed exactly Python message.
My router: D-Link DSL-504T
My UBUNTU: 5.10 (X86)
My adsl provider: ALICE (Italy)

Also the shell command 'ssh' works perfectly. I can log in on my University account from home.

Ciao.
!!!!  THANKS PYTHON  !!!!

Emanuele. Italy

---

### Post by stanigator on 2006-03-29
I'm totally new to linux. I have some problems modifying dhclient-script after commenting those lines out that you've suggested. Ubuntu wouldn't let me modify the file. Is there any solution to this? I'm using version 5.10 right now.

> **python]Go to COMPUTER--->SYSTEM CONFIGURATION--->NETWORKING (you will need to be superuser (root))

Then go to the DNS tab (probably 192.168.blah.blah as entry)

Find out your ISPs DNS nameservers, for example, Tiscali is 212.74.112.66 and 212.74.112.67.

Enter those bad boys in. Take 192.168.blah.blah OUT!



Then go to /etc/resolv.conf
Make sure that these two entries are there:

[COLOR=Red]nameserver 212.74.112.66
nameserver 212.74.112.67[/COLOR]

Your ISPs nameservers replacing mine  said:**
> # Modified for Debian.  Matt Zimmerman and Eloy Paris, December 2003

# The alias handling in here probably still sucks. -mdz

#make_resolv_conf() {
#    if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
#        local new_resolv_conf=/etc/resolv.conf.dhclient-new
#        rm -f $new_resolv_conf
#
#        if [ -n "$new_domain_name" ]; then
#            echo search $new_domain_name >> $new_resolv_conf
#        else # keep 'old' search/domain scope
#            egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> \
#                  $new_resolv_conf
#        fi
#        
#        if [ -n "$new_domain_name_servers" ]; then
#            for nameserver in $new_domain_name_servers; do
#                echo nameserver $nameserver >>$new_resolv_conf
#            done
#        else # keep 'old' nameservers
#            egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
#                  $new_resolv_conf
#        fi
#
#        chown --reference=/etc/resolv.conf $new_resolv_conf
#        chmod --reference=/etc/resolv.conf $new_resolv_conf
#        mv $new_resolv_conf /etc/resolv.conf
#    fi
#}[/COLOR]


That should have you sorted sunshine!

---

### Post by guysmiley on 2006-04-06
Yep,

From a terminal window type sudo gedit /etc/dhcp3/dhclient-script and this should do the trick.

NOTE:  This issue seems to arise almost exclusively with D-Link routers...  I'm not quite sure why.

---

### Post by neewfeeel on 2006-04-25
Am I the only one doomed to browse only my LAN?
I have done all of the above mods but I still can't get Firefox going out there!
Please help me!!!

Router is DSL-502T and Ubuntu 5.10
On the router config page I noticed I can't even get an host name and on startup I get the messages "temporary failure in name resolution" and the one about clock sync failure.

Ahem...I'm a newbie, so don't kick me too hard...:-(

---

### Post by neewfeeel on 2006-04-26
Ooops...my fault! I warned you I was a newbie ;-p

Tiscali DNS servers changed to 195.130.224.18 and 195.130.225.129
Now it's working fine!

Thanks a lot!!!
Bye

---

### Post by handy on 2006-05-01
Just another thankyou from me! Python :KS 

With a new Breezy install I did for someone recently.  I had to do the ipv6 thing in firefox, using about:config, to get it to browse the web.

Then I had to make your recommended modifications to get Automatix to be able to download.  I suspect the repositories became available at the same time! :KS   

This machine was also using the Netgear ADSL DG635 modem / router!  Which must be the reason why.  These people use a different ISP than me!

Thanks Again, & Again...

---

### Post by Brodie 1 Kenobi on 2006-07-12
This fixed me up straight away too. :D 

I had the same sort of problem with Breezy Badger, and basically left it untouched for 6 months. I have spent the last week struggling with Dapper Drake too.

I was able to Ping and Lookup site addresses in Network Tools to visit a site (temporarilly) to get this far until now (incase anyone is looking for a problem with that sort of nasty workaround). I have not yet restarted, but I am full of confidence now!

Love your work Python. Ubuntu just became usable (and it looks like you have helped covert many others).

Cheers!

[EDIT] - forgot to mention I have a Netcomm NB5Plus4 ADSL Modem/Router.

---

### Post by gmccague on 2006-08-29
> **python said:**
> Go to COMPUTER--->SYSTEM CONFIGURATION--->NETWORKING (you will need to be superuser (root))

Then go to the DNS tab (probably 192.168.blah.blah as entry)

Find out your ISPs DNS nameservers, for example, Tiscali is 212.74.112.66 and 212.74.112.67.

Enter those bad boys in. Take 192.168.blah.blah OUT!



Then go to /etc/resolv.conf
Make sure that these two entries are there:

[COLOR=Red]nameserver 212.74.112.66
nameserver 212.74.112.67[/COLOR]

Your ISPs nameservers replacing mine ;-P
Nameserver 192.168.blah.blah should either be commented out (preceded with a #) or not be there at all.



Finally, go to /etc/dhcp3/dhclient-script and comment out this:

[COLOR=Red]# Modified for Debian.  Matt Zimmerman and Eloy Paris, December 2003

# The alias handling in here probably still sucks. -mdz

#make_resolv_conf() {
#    if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
#        local new_resolv_conf=/etc/resolv.conf.dhclient-new
#        rm -f $new_resolv_conf
#
#        if [ -n "$new_domain_name" ]; then
#            echo search $new_domain_name >> $new_resolv_conf
#        else # keep 'old' search/domain scope
#            egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> \
#                  $new_resolv_conf
#        fi
#        
#        if [ -n "$new_domain_name_servers" ]; then
#            for nameserver in $new_domain_name_servers; do
#                echo nameserver $nameserver >>$new_resolv_conf
#            done
#        else # keep 'old' nameservers
#            egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
#                  $new_resolv_conf
#        fi
#
#        chown --reference=/etc/resolv.conf $new_resolv_conf
#        chmod --reference=/etc/resolv.conf $new_resolv_conf
#        mv $new_resolv_conf /etc/resolv.conf
#    fi
#}[/COLOR]


That should have you sorted sunshine!


This won't work with a notebook computer using DHCP. You are in effect disabling DHCP's assignments of the DNS Servers. I think it is better to disable ipv6 completely as so many ISPs are not anywhere near deployment of the protocol.

---

### Post by timothy_duncan on 2006-11-26
does this method works for dsl-302g?  im a newbie and dont want to edit heaps of this on my hardware that i dont understand..

---

### Post by bonehead on 2006-12-09
Hi I am a complete newbie with Linux and only just installed it on a computer a day ago.I have a Dlink DSL 504T router running with BTinternet as my ISP but cant seem to get connected to the internet do I have to go into the router settings and add new connection etc?I am add a complete lose over here and dont have a clue with what I am doing.

Regards,
Bonehead:confused:

---

### Post by Thornton_Reed on 2006-12-19
Hi all.

This procedure has been really useful to me in the past, on Slackware 10.2 and Ubuntu 6.06. However I have just upgraded to Ubuntu 6.10 and it doesn't work for me, I have to re-type the DNS Ip every 10 mins or so. I just don't understand because as I say it worked perfectly in the previous distros I have been using.

Does anyone have any ideas. My router is a DSL-504T and I'm on Tiscali.

Thanks :)

---

### Post by IGNIZ on 2006-12-26
unfortunately here i have the same problem with edgy...
i don't really know what to do

---

### Post by The_Wall512 on 2007-03-17
> **python said:**
> Go to COMPUTER--->SYSTEM CONFIGURATION--->NETWORKING (you will need to be superuser (root))

Then go to the DNS tab (probably 192.168.blah.blah as entry)

Find out your ISPs DNS nameservers, for example, Tiscali is 212.74.112.66 and 212.74.112.67.

Enter those bad boys in. Take 192.168.blah.blah OUT!



Then go to /etc/resolv.conf
Make sure that these two entries are there:

[COLOR=Red]nameserver 212.74.112.66
nameserver 212.74.112.67[/COLOR]

Your ISPs nameservers replacing mine ;-P
Nameserver 192.168.blah.blah should either be commented out (preceded with a #) or not be there at all.



Finally, go to /etc/dhcp3/dhclient-script and comment out this:

[COLOR=Red]# Modified for Debian.  Matt Zimmerman and Eloy Paris, December 2003

# The alias handling in here probably still sucks. -mdz

#make_resolv_conf() {
#    if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
#        local new_resolv_conf=/etc/resolv.conf.dhclient-new
#        rm -f $new_resolv_conf
#
#        if [ -n "$new_domain_name" ]; then
#            echo search $new_domain_name >> $new_resolv_conf
#        else # keep 'old' search/domain scope
#            egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> \
#                  $new_resolv_conf
#        fi
#        
#        if [ -n "$new_domain_name_servers" ]; then
#            for nameserver in $new_domain_name_servers; do
#                echo nameserver $nameserver >>$new_resolv_conf
#            done
#        else # keep 'old' nameservers
#            egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
#                  $new_resolv_conf
#        fi
#
#        chown --reference=/etc/resolv.conf $new_resolv_conf
#        chmod --reference=/etc/resolv.conf $new_resolv_conf
#        mv $new_resolv_conf /etc/resolv.conf
#    fi
#}[/COLOR]


That should have you sorted sunshine!


Hi everybody, in particoular Python for help us. 

But I have a little (or big, i don't know) problem about the DNS Servers. It appens that the numbers I put disappear automatically after few minutes and reappears 198.162.ecc ecc. so internet doesn't work again. 

What I have to do? I'll thanks everyone answer me.

       Lorenzo 

P.S.: another strange thing: I have Libero ADSL but internet work also with Tiscali DNS Servers..

---

### Post by quincywalltech on 2007-10-17
When setting up a ADSL router we forget to set the DNS servers and let the ISP set them which can slow down the connection.

A lot of times a slow connection is realy the DNS servers, your are using - are overloaded. Most isp's run a standard BIND server that is very veunerable to floods that can be common with older Linksys routers. 

[http://www.DNSServerList.org]("http://www.DNSServerList.org") has daily updated servers that are open to the public.

Try changing your DNS servers on your router to these. 

Also note that if you have a Linksys (Or other router with three DNS slots) populate all three.

Helpfull sites.
[http://www.DNSServerList.org]("http://DNSServerList.org")
[http://www.Open-DNS.org]("http://Open-DNS.org")
[http://www.IPGeoLocator.com]("http://www.IpGeoLocator.com")
Enjoy
QW

---

### Post by CrazyKev on 2007-11-06
Hi all.

Followed Python's excellent advise to the letter but have 2 problems. Firstly which ever DNS server that I choose, after a time or after a reboot it resets to the typical 192.168.blah.blah. Therefore I have to keep resetting it back. The other problem (which might be the reason) is I can't find the dhclient-script file to comment out. All I have in the suggested directory is dhclient.conf which when opened is different and has nothing to comment out.

I have tried saving the new DNS IP address but it makes no difference - it still resets.

Anybody know what's going wrong?

---

