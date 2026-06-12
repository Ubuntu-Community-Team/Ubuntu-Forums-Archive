---
title: "adding a linux webserver onto a network"
date: 2005-11-16
forum: General Help
---

### Post by spyke01 on 2005-11-16
ok, i have a tree topology network, it may grow to several tiers, its being run by a dsl modem

the asci art style setup ^^

modem
   |
   | crossover cable
   |
switch
  |  |  |
  |  |  |
  |  |  Server
  | PC
 PC 

The Server:
Apache
MySQL
PHP
Perl
GD And PEAR Libraries


i guess basiclly my question is, if i just add it onto my switch like above, and run apache will it be accesible from the internet? how can i check the external ip address of this pc? also can i use the webserver as an intranet server too?

---

### Post by guX on 2005-11-16
I don't think it'd be accessible from the internet, but you could set up your modem to forward port 80 to the IP address of the web-server, and then it should work.

---

### Post by oskude on 2005-11-16
[QUOTE=spyke01]i guess basiclly my question is, if i just add it onto my switch like above, and run apache will it be accesible from the internet?[/QUOTE]yes, if your dsl-modem (without router) can call to ISP
yes, if your dsl-modem (with router) can call to ISP. open port 80 for the IP of your server
yes, if you make the connection with PC, you have to route through that PC.

[QUOTE=spyke01]how can i check the external ip address of this pc?[/QUOTE]curl "http://www.networksecuritytoolkit.org/nst/cgi-bin/ip.cgi"

[QUOTE=spyke01]also can i use the webserver as an intranet server too?[/QUOTE]
yes, just use the servers IP

---

### Post by basketcase on 2005-11-16
Could also try dyndns.com if you don't get a static IP with your DSL

---

### Post by spyke01 on 2005-11-16
[QUOTE=oskude]yes, if your dsl-modem (without router) can call to ISP
yes, if your dsl-modem (with router) can call to ISP. open port 80 for the IP of your server
yes, if you make the connection with PC, you have to route through that PC.

curl "http://www.networksecuritytoolkit.org/nst/cgi-bin/ip.cgi"


yes, just use the servers IP[/QUOTE]

what do you mean by call the ISP and open port 80, does this mean open port 80 on the dsl modem with router's firewall?

---

### Post by oskude on 2005-11-16
didnt see any router in your network-tree...

do you have a dsl-router ? (not just dsl-modem)
in that case just open the port 80 in the dsl-routers firewall and address it to the servers IP

---

### Post by spyke01 on 2005-11-16
yep, its a dsl router and modem built into one
ok, is it possible to have this box running apache for the webserver part, and something else for the intranet side?

---

### Post by oskude on 2005-11-16
[QUOTE=spyke01]is it possible to have this box running apache for the webserver part, and something else for the intranet side?[/QUOTE]yes.

as you open only port 80 to be accessible from internet, you could run "something else" on another port...

---

### Post by spyke01 on 2005-11-16
is it possible to run 2 apaches?

---

### Post by kruz on 2005-11-16
yes but since you ARE only assigned one IP
you would need to run one on
publicip:80
and publicip:81 or w/e port u want

when u setup a webpage, like .cjb.net
you can set it up on different ports
this is how hosting companys can host ur website, and 10 others
on the trial account :D

so basically try it go to [www.cjb.net](www.cjb.net) i think it is
or wandoiuwnaoids.cjb.net will take u there
register one like mynewawesomecomputer.cjb.net
make ur ip adress that + port 80
ex : 284.142.12.4:80
then one will be
284.142.12.4:81
that will lead to the other machine if you have port forwarding to one ip
and the other port to another

cheers!

---

### Post by spyke01 on 2005-11-16
awesome thanx man

---

### Post by kruz on 2005-11-16
[QUOTE=spyke01]awesome thanx man[/QUOTE]


no prob
hope it makes more since now

if it doesnt just pm me or make a new thread
the concept took me awhile to understand
with the port forwarding jumbo
apache on differnet ports
alot to handle if routing is new to you

but u look like u got it under control

---

