---
title: "[SOLVED] why doesnt gconftool-2 work with su?"
date: 2008-10-28
forum: General Help
---

### Post by subes on 2008-10-28
Hi,

i wrote a small networkmanager script that enabled/disables the proxy depending on the vpn connection state...

Im using gconftool-2 in that script to set the gconf values

The is placed as /etc/NetworkManager/dispatcher.d/02vpnproxy
and is executable.

```
#!/bin/bash

#Diese Werte werden vom NetworkManager an das Skript übergeben
INTERFACE=$1
ACTION=$2

#Hauptbenutzer finden
ON_USER=$(cat /etc/passwd | grep :1000: | cut -d ':' -f 1)

#echo $ON_USER

## Funktionen durchführen, je nach Aktion eine andere
case "$2" in
        vpn-up)
                gconftool --type string --set /system/proxy/mode manual
                gconftool --type boolean --set /system/http_proxy/use_http_proxy true
                su $ON_USER -c 'gconftool --type string --set /system/proxy/mode manual && gconftool --type boolean --set /system/http_proxy/use_http_proxy true'
                ;;
        vpn-down)
                gconftool --type string --set /system/proxy/mode none
                gconftool --type boolean --set /system/http_proxy/use_http_proxy false
                su $ON_USER -c 'gconftool --type string --set /system/proxy/mode none && gconftool --type boolean --set /system/http_proxy/use_http_proxy false'
                ;;
        *)
                echo $"Usage: $0 {vpn-up|vpn-down}"
                ;;
esac

```

The problem i have, is that the gconf values or not set
when i issue the commands as the normal user in console, the values get updated.
When login as root via "sudo su" and use "su <USER> -c '...'" the values are not updated.
Tho, when i login as root via "su" instead of "sudo su", the command works fine.
Why doesnt gconftool work all the time? It doesnt even print any errors.

Is there some better way to change the proxy via the networkmanager dispatcher and gconf?
Or why doesnt the script "just work"?

Ive tried quite some stuff, but im on a complete loss atm :(

---

### Post by peitschie on 2008-10-29
Hi there,

I experienced the same problem.  I am quite positive this is a bug as it previously behaved properly under Hardy.  I have filed this as [bug#290647](https://bugs.launchpad.net/gconf/+bug/290647) .  You might want to subscribe yourself to this and monitor its progress for a fix.

The workaround (though very hacky) is to call 'gconftool-2 --shutdown' after you finish all you're updates... I have no idea of the long-term impact of doing this however!

---

### Post by Yellow Pasque on 2008-10-29
When you call the command with sudo, it is probably changing the values for the root account (i.e.  you are changing /root/.gconf )

---

### Post by peitschie on 2008-10-29
Hi Temüjin,

While normally this would be the case, on this occassion a user id is being passed to su.

From the man pages:
```
su [options] [LOGIN]
```

So the su command is actually changing to the passed user ID... you can verify this yourself quite easily by running
```
su $USER -c 'echo $USER'
``` which should echo your username.  So when doing this, gconf will definitely be updating the su'ed user, not root.

---

### Post by sdennie on 2008-10-29
I run gconftool-2 commands from automated scripts as root using this method:

```

**DISPLAY=:0.0** su my_username -c "gconftool-2 ..."

```

It's been some time since I've tried it without setting DISPLAY like that but, I believe it is needed.

---

### Post by peitschie on 2008-10-29
Actually subes, I notice you are using 'su'... perhaps try the script with 'sudo -u username <command>' instead?  Also, what release of Ubuntu are you currently running?

---

### Post by subes on 2008-10-29
forgot to mention, im using intrepid.

thanks for yor replies so far, ill be able to try your suggestions later this evening, when i have time for this.

ill report back about my success *hopefully* :)

---

### Post by subes on 2008-10-29
well, i tried giving the DISPLAY env variable, sudo and gconftool --shutdown alone and in all different combinations.

none of those fixed my problem :(

the only way this works is:
im logged in from console as "subes"
i type in "su" and login as root
then i run the script and everything is updated

when logging in as root with "sudo" instead of "su" the script doesnt work.
it also doesnt work when calling the script with sudo <script>, tho when callind the script with su -c <script> it works fine.

and networkmanager itself runs as root, but the script has no effect even tho it is running

---

### Post by peitschie on 2008-10-29
Ok, the problem as identified upstream is that there has been a change in how dbus stores its sessions.  This means the latest version needs to be told which session to use, else it simply creates a new one!

Subes, to make your script work again you need to retrieve the dbus session address.  The modified version of your code (also uses sudo now...) would be thusly:

```

#!/bin/bash

#Diese Werte werden vom NetworkManager an das Skript übergeben
INTERFACE=$1
ACTION=$2

#Hauptbenutzer finden
ON_USER=$(cat /etc/passwd | grep :1000: | cut -d ':' -f 1)
#Assumes user directory is /home/$ON_USER
export DBUS_SESSION=$(grep -v "^#" /home/$ON_USER/.dbus/session-bus/`cat /var/lib/dbus/machine-id`-0)

#echo $ON_USER

## Funktionen durchführen, je nach Aktion eine andere
case "$2" in
        vpn-up)
                gconftool --type string --set /system/proxy/mode manual
                gconftool --type boolean --set /system/http_proxy/use_http_proxy true
                sudo -u $ON_USER $DBUS_SESSION gconftool --type string --set /system/proxy/mode manual
                sudo -u $ON_USER $DBUS_SESSION gconftool --type boolean --set /system/http_proxy/use_http_proxy true

                ;;
        vpn-down)
                gconftool --type string --set /system/proxy/mode none
                gconftool --type boolean --set /system/http_proxy/use_http_proxy false
                sudo -u $ON_USER $DBUS_SESSION gconftool --type string --set /system/proxy/mode none
                sudo -u $ON_USER $DBUS_SESSION gconftool --type boolean --set /system/http_proxy/use_http_proxy false
                ;;
        *)
                echo $"Usage: $0 {vpn-up|vpn-down}"
                ;;
esac

```

I've now got this running on my own setup properly

---

### Post by subes on 2008-10-30
thank you very much! now it worx :)

---

### Post by subes on 2008-10-30
I noticed that the proxy doesnt get deactivated when doing a shutdown with an active vpn connection

so i added this line to "/etc/rc.local": 

```
bash /etc/NetworkManager/dispatcher.d/02vpnproxy ppp0 vpn-down
```

this deactivates the proxy on boot
so only when connecting to vpn, the proxy will be activated again

*edit --------------

putting this into rc.local doesnt work because of the gconf deamon not running for the main user.
the fix for this is to put this into the session startup of gnome under System -> Settings -> Session

command: /etc/NetworkManager/dispatcher.d/02vpnproxy ppp0 vpn-down

---

