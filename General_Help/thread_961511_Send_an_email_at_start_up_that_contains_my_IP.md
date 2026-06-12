---
title: "Send an email at start up that contains my IP"
date: 2008-10-28
forum: General Help
---

### Post by George7a on 2008-10-28
Hi,

I would like to create a job in ubuntu that will be executed whenever my system is up. This job's job is to send me an email that contains my I.P. address.

How can I do that?

- George

---

### Post by brandon88tube on 2008-10-28
I am not sure if you can display the IP that is shown on the internet. I do know that you can show the physical IP by doing ifconfig.

---

### Post by pluckypigeon on 2008-10-28
> **George7a said:**
> Hi,

I would like to create a job in ubuntu that will be executed whenever my system is up. This job's job is to send me an email that contains my I.P. address.

How can I do that?

- George

Not sure what you mean but you could set your web browser's home page to whatismyipaddress.com and have it open at start up.....

---

### Post by Portmanteaufu on 2008-10-28
I'm not sure whether you're trying to get at your box's IP address behind your router or the IP address of your router itself. If it's the former, you could use a bash command like the following:

ifconfig | grep -Po "inet addr:.+Bcast" | grep -Po '(?:\d{1,3}\.){3}\d{1,3}'

to get the IP addresses listed by ifconfig. Getting your router's external IP address would be a more involved process.

Once you have a script, follow these instructions to get it to run at boot time: 

[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by Herman on 2008-10-28
:) Thanks for sharing that link about hot to get a script to run at start-up, Portmanteaufu. I like that, I'll give it a try.

George7a, 
I have a 'roving IP address', (for my router, but inside my LAN, my computers' IP addresses remain the same), and I wanted to be use SSH to network into my home computer from anywhere in the world. [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm")**.**

I don't want to go to the work of setting up a [COLOR=#000000][DynamicDNS]("https://help.ubuntu.com/community/DynamicDNS") - Ubuntu Community Documentation, or, [Dynamic DNS No-IP]("http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html").[/COLOR] (But those links do explain some good ideas, maybe I will try some of those tricks later, some other day).

All emails contain the sender's external IP address (the router's address on the internet, as seen by [http://www.whatismyipaddress.com/](http://www.whatismyipaddress.com/)), but most people don't know where to look for it. 
If you want to find it, open the email and click 'View'-->'Message Source', and the sender's IP address will be there somewhere.
At my place, the external IP is supposed to remain the same for as long as the router is up, but mine changes about once every hour for some reason, (I think I have a faulty 'phone line), so in my case, the email needs to be very recent for this to work. For most people it should be easier.

[COLOR=#000000]There are several programs that can be used to send email from the command line, and that means they can be set up in a crontab to cause them to be send out at regular intervals, or any times we decide to set.
The email program I use is '[sendEmail]("http://caspian.dotconf.net/menu/Software/SendEmail/")'.

SendEmail can be installed with apt-get or Synaptic in Ubuntu and it is quite simple to use.
[/COLOR]                     ```
sudo apt-get install sendemail                   
```Here's how to send an email to yourself with sendEmail, from the command line,
example,
 ```
sendEmail -f [EMAIL="user@bigpond.net.au"]user@bigpond.net.au[/EMAIL] -t [EMAIL="user@bigpond.net.au"]user@bigpond.net.au[/EMAIL] -o message-file=hello.txt -v -s mail-hub.bigpond.net.au
```                   Where: -f [EMAIL="user@bigpond.net.au"]user@bigpond.net.au[/EMAIL] is the email address it's being sent **f**rom
Where: -t [EMAIL="user@bigpond.net.au"]user@bigpond.net.au[/EMAIL] is the email address it's being sent **t**o
Where: after the -o option, hello.txt is a plain text file containing a message.
Just make your own text file with any message in it. It doesn't matter what the message contains. 
Maybe send your self a reminder of what port numbers your home router is using for each PC's SSH port to make it useful.
Where: -s is your mail **s**erver, that depends on your ISP.

Now that you know how to send yourself an email from the command line, you can probably figure out how to use crontab to do the same thing. If you don't know how to set up crontab, look here: [Configure 'crontab']("http://users.bigpond.net.au/hermanzone/p13.htm#Use_crontab")

How to send an email to yourself with sendEmail, from crontab,
example,
                    ```
0 6 * * *  /usr/bin/sendEmail -f [EMAIL="user@bigpond.net.au"]user@bigpond.net.au[/EMAIL] -t [EMAIL="user@bigpond.net.au"]user@bigpond.net.au[/EMAIL] -o message-file=hello.txt -s mail-hub.bigpond.net.au
``` Where: you will send your self an email at 06:00 every day. You might want to make more of these. One every four hours or very six hours or eight hours or whatever.

Regards, Herman :)

---

### Post by Portmanteaufu on 2008-10-28
And thank *you*, Herman, for that tip on finding an IP address in an e-mail. I'd never thought to do that, that's invaluable!

I just checked on whatismyip.com, and they have a service that provides a page with -just- your IP address and no other markup.

If you run: 

wget -q -O - [http://whatismyip.com/automation/n09230945.asp](http://whatismyip.com/automation/n09230945.asp) && echo -en '\n'

It will dump your external IP address to standard out, which is pretty useful for scripting. I don't know, though, if that's the permanent link or not. If it changes on a regular basis, it's obviously less helpful.

---

### Post by George7a on 2008-10-29
Thank you guys for all your help, I totally forgot about sendmail I thought I will be using the open office application.

I think I have everything I need to test this. I will try all of that when I get home.

thanks again,

- George

---

### Post by brandon88tube on 2008-10-29
> **Portmanteaufu said:**
> It will dump your external IP address to standard out, which is pretty useful for scripting. I don't know, though, if that's the permanent link or not. If it changes on a regular basis, it's obviously less helpful.

Well, if you really need to you can just make your own php script that says your IP, which is pretty easy.

---

### Post by Portmanteaufu on 2008-10-29
> **brandon88tube said:**
> Well, if you really need to you can just make your own php script that says your IP, which is pretty easy.

True! Just a couple of lines at most. Sadly, in order to get your external IP you'd have to have someplace to host the script outside your network, which not everyone has.

---

### Post by Herman on 2008-10-29
Just to bring all of this together and clarify it a little for those who are trying to follow this thread but are still new at using the command line,
```
#!/bin/bash
# a script for sending myself an email containing my IP address

echo "My external IP address is:" >> whereami.txt ; wget -q -O - http://whatismyip.com/automation/n09230945.asp >> whereami.txt
echo " " >> whereami.txt
echo " " >> whereami.txt
echo "My internal IP address is:" >> whereami.txt ; ifconfig | grep -Po "inet addr:.+Bcast" | grep -Po '(?:\d{1,3}\.){3}\d{1,3}' >> whereami.txt

sendEmail -f username@bigpond.net.au -t username@bigpond.net.au -o message-file=whereami.txt -v -s mail-hub.bigpond.net.au
```I tested the above script and it worked well for me, thanks again to Portmanteaufu for the brilliant commands. :)
It's much more graceful and civilized to have the IP address in the email message rather than requiring a user to view the message source.

As you can see, I'm still a newbie at bash scripting myself, I had to make an empty echo command or two to get the lines spaced the way I wanted, (LOL!).

I just wanted to add here that it's possible to run programs and scripts from your Evolution calendar automatically at certain times and/or dates by setting them to run from a custom alarm. (Similar to Kalarm). Some people might prefer to do it that way as an alternative to setting up crontab. 
Here's a link about that, [Memos, Tasks and Calendar Appointments]("http://users.bigpond.net.au/hermanzone/p5.htm#Memos_Tasks_and_Calendar_Appointments").

This way if you're planning to travel between certain dates, you can use your evolution calendar to schedule your script to run at the required times. You need to test this well before-hand to make certain everything will work, because Gnome will ask for permission the first time it run each script or program for the first time.
Before leaving, we would need to set our home computer to not automatically receive email every ten minutes, or to leave (a copy of) the email on the server.
Once that's set up and tested we can go traveling with our Ubuntu-EeePC or Ubuntu in a USB flash memory stick and still have access to all of our files in our home computer through SSH, providing of course our home or office computer remains up and running while we're away. :)
EDIT: Also providing SSH Server is installed and port forwarding is set up between the ADSL modem/router and the user's computer in the LAN. See: [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm").

---

### Post by George7a on 2008-11-01
Thanks again for everyone!

I did some modification to the script so that it will delete the older file and use Gmail. Here is my final script.
```

#!/bin/bash
# a script for sending myself an email containing my IP address
if [ -f ./whereami.txt ]
then
rm ./whereami.txt
fi

date >> ./whereami.txt
echo " " >> ./whereami.txt
echo "My external IP is" >> whereami.txt ; wget -q -O - http://whatismyip.com/automation/n09230945.asp >> whereami.txt

sendEmail -u "Ubuntu is UP - IP" -f ***@gmail.com -t ***@gmail.com -o message-file=whereami.txt -v -s smtp.gmail.com -xu ***@gmail.com -xp *** -o tls=yes

```

Thanks to all again,

- George

---

### Post by George7a on 2008-11-01
When I tested the script it worked great. I have also change the "./" to the full path in my script.

I have edited my crontab. The following is the result of crontab -l:
> # m h  dom mon dow   command
@reboot bash /home/george/ip2email

When I rebooted my system for my final test, I got an email but the IP was not there!](*,)](*,)

It seems that script failed to get the external IP. One reason I could think of that I am not sure whose "job" runs first!. Is it the cron, or the internet connection.

Any other ideas / workarounds?

- George

---

### Post by George7a on 2008-11-01
I have found a way!

I used the command "sleep". The wierd thing was when I used this command in the script, the script did not get the IP. So I wrote another wrapper script that waits for 60 seconds then activate the old script
wrapper script code:
```

#!/bin/bash
# a script for sending myself an email containing my IP address
sleep 60
bash /home/george/main.ip2email

```
- George

---

### Post by George7a on 2008-11-01
Still not solved!

I checked the email that was sent on startup but it wasn't my external IP!!!!:shock::shock:

I ran the script manually again, and it did send the right IP!

Why is it getting another IP?!

Any ideas? Shall I wait more than a minute then send the email?

---

### Post by George7a on 2008-11-01
I think that the 3 minutes is working, but I have bumped into another problem. I hope this one is the last one!

Getting the IP via the wget command is not stable. I have modified it to check what was the reason and I got this log:
> --07:35:19--  [http://whatismyip.com/automation/n09230945.asp](http://whatismyip.com/automation/n09230945.asp)
           => `-'
Resolving whatismyip.com... 72.233.89.198, 72.233.89.200, 72.233.89.199
Connecting to whatismyip.com|72.233.89.198|:80... connected.
HTTP request sent, awaiting response... 503 Service Unavailable
07:35:19 ERROR 503: Service Unavailable.

However, I can extract the IP from the email that I got by looking into the original message. But I would like to see it in the emails body.

Is there another way to get the External IP address?

---

### Post by George7a on 2008-11-03
Any idea why I am getting error 503 from [http://whatismyip.com?](http://whatismyip.com?)

Is there another idea to get the external IP address?

---

### Post by kurtymckurt on 2008-11-03
> **George7a said:**
> Hi,

I would like to create a job in ubuntu that will be executed whenever my system is up. This job's job is to send me an email that contains my I.P. address.

How can I do that?

- George

Do do a start upscript make a file similar to this and put it in /etc/init.d/

```

case "$1" in
    start)
        echo "COMMAND RUN"
        run command
        echo "OK"
        ;;
    stop)
        #doesn't need to do anything
        ;;
    reload|restart)
        $0 stop
        $0 start
        ;;
    *)
        echo "Usage: $0 start|stop|restart|reload"
        exit 1
esac
exit 0

```

then run 

```
update-rc.d /etc/init.d/nameoffile defaults 
```

use man update-rc.d to make use of more options!

---

### Post by pauljz on 2008-11-03
You may find it quite a lot easier to go with a Dynamic DNS provider, as mentioned by an earlier poster.

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

No need to reinvent the wheel when good free systems for this already exist.  Many home routers/cable modems even support this out of the box, sparing you the need to configure this regularly on whatever systems you have running at the time.

---

### Post by George7a on 2008-11-03
But I do not have a domain! And I am not willing to buy one soon.

I only need my external IP.

---

### Post by howefield on 2012-03-24
Closed.

---

