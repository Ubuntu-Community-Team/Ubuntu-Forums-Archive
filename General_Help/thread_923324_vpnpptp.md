---
title: "vpn/pptp"
date: 2008-09-18
forum: General Help
---

### Post by hethemystery on 2008-09-18
hi

i recently installed wubi. first of all i dont know if it downloaded the complete iso or not but its installed. now i got 2 problems which i cant figure out after google these propblems.

1 - vpn/pptp
2 - resolution

1 - vpn/pptp

it is not available in my distribution. i searched it in application>add/remove it wasnt available there. than i tried few commands in terminal as i found on other sites but terminal shows no such commands available.

is there any solution if i can download any package or something and install it??

2 - resolution

currently my resolution is 600x800 i want to increase it to 1050x800 same as windows. i searched alot about it but failed to find any solutin in wubi. than i searched web and found few commands and asusual terminal says no such commands available.

can anyone please help me out with these 2 problems.

Note: i am new to linux.

---

### Post by zajc on 2008-09-18
1.) Install **network-manager-pptp** and then in network-manager VPN sub menu appeared

```
sudo apt-get install network-manager-pptp
```

2.) Try to install "restricted drivers" if this will help

System-> Administration-> Hardware drivers

---

### Post by Orlsend on 2008-09-18
> **zajc said:**
> 1.) Install **network-manager-pptp** and then in network-manager VPN sub menu appeared

```
sudo apt-get install network-manager-pptp
```

2.) Try to install "restricted drivers" if this will help

System-> Administration-> Hardware drivers
You could try that or if that does nto work search in **add/remove** for KVpnc.

Lets you mange all VPN types.

---

### Post by hethemystery on 2008-09-18
hi 

thanks for reply. this is the reply i got in terminal:

"E: could not find package network-manager-pptp"

there is nothing in add/remove with name Kvpnc or PPTP 
network-manager is already installed. no upgarde required.

for hardware drivers i need internet connection which is not possible until i install pptp package or vpn.

is there any package available which i can download while staying in windows and than install it in wubi??

please guide me how to solve this problem.

---

### Post by Orlsend on 2008-09-19
I think your repo lists are outdated.

anyways here is KVpnc

[http://home.gna.org/kvpnc/en/index.html](http://home.gna.org/kvpnc/en/index.html)

---

### Post by hethemystery on 2008-09-19
thanks orlsend

even its not installing. 

it gave error

"dependencies are insufficient"

i downloaded this file. restarted my system in wubi/ubuntu. located this file and than double click it. and got error.

i cant update anything else just becaue i cant connect to my server without vpn/pptp. my network have given solution for linux  as in fedora and sussie but nothing about ubuntu. 

i dont know how to run pptp and get connected to my server. its actually a lan network to access internet we have to dial (VPN)and get connected to the server.

to local sites i can access through firefox but i cant access internet at all.

i have installed the latest version of wubi.

i will really appreciate your help if you can solve my problem.

---

### Post by Orlsend on 2008-09-20
Ok I found what you are looking for, just search "VPN" in the Synaptic Package Manger look at the list and there i should be the one for VPN/PPTP

---

### Post by hethemystery on 2008-09-20
thanks orlsend

i really appreciate your help

i did search in Synaptic Package Manger and vpn was empty no results so i did refresh and it started downloading but failed to download as i cant download anything from internet until i connect to my server through vpn/pptp

so i searched the same file from this site 

[http://packages.ubuntu.com/hardy-updates/i386/openvpn/download](http://packages.ubuntu.com/hardy-updates/i386/openvpn/download)

and tried to install openvpn but it gave same error of dependencies

i even downloaded kvpnc and same error of dependencies

i really wonder how to solve this problem. i have been searching google all the time but at no place i found any solution or procedure to install it.

---

