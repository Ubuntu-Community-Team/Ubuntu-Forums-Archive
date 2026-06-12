---
title: "Hotmail upgrade in 9.04 with Evolution, &quot;Couldn't find package hotway&quot;"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by clyde9999 on 2009-04-13
Trying to add Hotmail to Evolution, and the "hotway" package could not be found for installation. 

> Couldn't find package hotway


I truly appreciate any assistance. It works great in the other distro's.

clyde9999

---

### Post by clyde9999 on 2009-04-16
Has anyone had luck with Hotmail and Jaunty Jackalope? I have not! Not able to find the package Hotway..

---

### Post by clyde9999 on 2009-04-24
I guess that I will just have to continue to look for "hotway". Not sure why it is not added to the Ubuntu repositories like it is in past versions.

Jack

---

### Post by clyde9999 on 2009-04-24
I installed the package from here:
[http://packages.ubuntu.com/hardy/mail/hotway](http://packages.ubuntu.com/hardy/mail/hotway)

---

### Post by nerosbookshelf on 2009-04-29
Clyde,
 
If you don't mind, how exactly did you install that package? I'm a linux newby. I used 8.1 before and installing hotway was easy as there are enough instructions around. I tried to fiddle around with the package found on the site you linked to, but I cannot get it installed in jaunty...

---

### Post by lixinran on 2009-04-29
We don't really need hotway anymore. pop3 service for hotmail is free now. So just set up as regular way. :popcorn::lolflag:

---

### Post by metalhawk83 on 2009-04-29
I can't really find a way to set up POP3 accounts in evolution guys. It doesn't even give me the option. In addition, even after installing hotway, evolution just won't cooperate and download mail from hotmail. Do you have any ideas why?

---

### Post by metalhawk83 on 2009-04-29
I finally have it working now. Check here for a solution [http://www.ubuntugeek.com/how-to-configure-evolution-to-use-hotmail-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-configure-evolution-to-use-hotmail-in-ubuntu-810-intrepid-ibex.html)
It worked for me in Jackalope!

---

### Post by Paresh on 2009-04-30
Now that pop3 is available FOC from Hotmail, you can amend your evolution account:-

Receiving email
Server Type = POP
Server = pop3.live.com
Secure Connection = SSL encryption

Sending email
Server Type = SMTP
Server = smtp.live.com
Secure Connection = TLS encryption

All other settings stay the same.

Not sure why TLS works for sending and SSL for receiving, but this is what worked for me.

The only thing is that it does seem to download all messages on the server, even if they were downloaded previously.

More info [here]("http://windowslivehelp.com/solutions/settings/archive/2009/01/06/send-and-receive-windows-live-hotmail-emails-from-a-mail-client.aspx")

---

### Post by clyde9999 on 2009-05-01
> **Paresh said:**
> Now that pop3 is available FOC from Hotmail, you can amend your evolution account:-


It is a good thing, I was not able to get hotway to work anyway. I will set it up using pop3. Sorry for not responding sooner.

Jack

---

### Post by clyde9999 on 2009-05-01
> **Paresh said:**
> Now that pop3 is available FOC from Hotmail, you can amend your evolution account:-

Receiving email
Server Type = POP
Server = pop3.live.com
Secure Connection = SSL encryption

Sending email
Server Type = SMTP
Server = smtp.live.com
Secure Connection = TLS encryption

All other settings stay the same.

Not sure why TLS works for sending and SSL for receiving

This is wonderful, Works great!!

Jack

---

### Post by dwouters on 2009-05-04
> **Paresh said:**
> Now that pop3 is available FOC from Hotmail, you can amend your evolution account:-

Receiving email
Server Type = POP
Server = pop3.live.com
Secure Connection = SSL encryption

Sending email
Server Type = SMTP
Server = smtp.live.com
Secure Connection = TLS encryption

All other settings stay the same.

Not sure why TLS works for sending and SSL for receiving, but this is what worked for me.

The only thing is that it does seem to download all messages on the server, even if they were downloaded previously.

More info [here]("http://windowslivehelp.com/solutions/settings/archive/2009/01/06/send-and-receive-windows-live-hotmail-emails-from-a-mail-client.aspx")

Thanks, Paresh. i've been looking for this solution for months. You da man.

---

### Post by NlCK on 2009-05-04
Great!!! 

Since when did pop3 for hotmail become free of charge? I tried to use hotmail on Evolution about a month ago and couldn't get it to work, so I gave up!

---

### Post by ensenadaubuntulover on 2009-05-14
> **Paresh said:**
> Now that pop3 is available FOC from Hotmail, you can amend your evolution account:-

Receiving email
Server Type = POP
Server = pop3.live.com
Secure Connection = SSL encryption

Sending email
Server Type = SMTP
Server = smtp.live.com
Secure Connection = TLS encryption

All other settings stay the same.

Not sure why TLS works for sending and SSL for receiving, but this is what worked for me.

The only thing is that it does seem to download all messages on the server, even if they were downloaded previously.

More info [here]("http://windowslivehelp.com/solutions/settings/archive/2009/01/06/send-and-receive-windows-live-hotmail-emails-from-a-mail-client.aspx")

FOR JAUNTY JACKALOPE

THIS IS IT 

worked like a charm and i spent sometime triing to get the hotway program which proved to be unnecesary

---

### Post by Siffle on 2009-05-15
hey guys, I'm brand new to Ubuntu and Linux.  I tried setting up my hotmail numerous times with the settings you listed but mine still isn't working.  When I hit send/receive in evolution, it opens a pop-up for my pop3.live.com password.  I enter it (my hotmail password I can only assume) but just says error while fetching mail.  Any ideas?

---

### Post by Paresh on 2009-05-15
Yes it is your hotmail password that is required.

can you give a little more info about the error (eg paste the text + any code numbers etc)?

I assume you have double checked that you have entered the details correctly.

Can you access your hotmail account using another method (eg using a browser?  That would at least confirm that your hotmail is running and the problem is with the evolution setup.

---

### Post by Siffle on 2009-05-15
I wish I could give more details but it simply says "error while Fetching Mail" at the bottom-left of the screen.  I enter my hotmail password and it just opens the enter password thing again.  Hotmail works fine in browser and on my other computer with Vista.  My administration password is the same as my hotmail password so it can be the only one to enter.

So I hit "send/receive" and I get:
The enter password screen that pops up for me is "Unable to connect to POP server pop3.live.com.  Error sending password - ERR authentication failed

I enter my hotmail/administrator password and it just pops up the same enter password again.  After I enter it a second time, it all goes away and just says the "error while Fetching Mail"

I'm stumped.  And yes, I've tried reentering the setting numerous times.

---

### Post by dwouters on 2009-05-15
Siffle,

The only other thing other than settings I can think of that would prevent you from getting your hotmail via this method is your behind a firewall. If this is the case, adjust your firewall settings. Looking at the firewall log should give you an idea of where the issue may be. Most likely, blocked port.

---

### Post by dwouters on 2009-05-15
> **NlCK said:**
> Great!!! 

Since when did pop3 for hotmail become free of charge? I tried to use hotmail on Evolution about a month ago and couldn't get it to work, so I gave up!

Nick,

It was about that time. I believe it was when they officially released Windows Live Mail. But these settings are working for me perfectly.

---

### Post by Paresh on 2009-05-16
Siffle

I agree with dwouters, if that's not the problem, I don't know what else it could be.  You could try the link I provided and see if there is something else there that may help, but I'm afraid you've reached the end of my knowledge in this area

---

### Post by angol on 2009-05-17
Not sure if this helps, but did you enter your full hotmail address i.e. [email]username@hotmail.com[/email] as"username", or just the username without the @ bit?

---

### Post by Paresh on 2009-05-18
It should be the full hotmail address > username@hotmail.com

---

### Post by crjackson on 2009-05-18
The settings work fine for pulling in the email, but it doesn't work for sending (for me anyway). I have to put in im ISP's SMTP server vs. **smtp.live.com** otherwise I can't send out mail.

---

### Post by RubBA on 2009-05-18
I've got another problem.
all settings seem to work i can receive and send mail but evolution keeps on making copies of al my mails. Wich resulted in a mailbox with 10.000+ e-mails.

Anyone any idea how to fix that?

---

### Post by crjackson on 2009-05-18
> **RubBA said:**
> I've got another problem.
all settings seem to work i can receive and send mail but evolution keeps on making copies of al my mails. Wich resulted in a mailbox with 10.000+ e-mails.

Anyone any idea how to fix that?

It sounds like you don't have it set to delete the messeges from the server after downloading.

---

### Post by dwouters on 2009-05-19
> **crjackson said:**
> The settings work fine for pulling in the email, but it doesn't work for sending (for me anyway). I have to put in im ISP's SMTP server vs. **smtp.live.com** otherwise I can't send out mail.

Make sure your smtp.live.com encryption is set to TLS encryption. Any other setting, the server will reject. Double check and make sure the setting are exactly as in the original post. Also, the user name for your outgoing server should be your full email address as well, i.e "username@hotmail.com" or "username@live.com". I use both of these and have no issues. Hope this helps.

---

### Post by RubBA on 2009-05-19
> **crjackson said:**
> It sounds like you don't have it set to delete the messeges from the server after downloading.
Yeh thats right i did uncheck the box wich says delete the messages from server after downloading. I did that because i want to be able to read my mail from other workstations too, or is that also possible when i do check that box?  Still its strange, the mail client should know when a certain message has already been downloaded and skip them, even if they are stil on the server, not?

---

### Post by RubBA on 2009-05-19
> **dwouters said:**
> Make sure your smtp.live.com encryption is set to TLS encryption. Any other setting, the server will reject. Double check and make sure the setting are exactly as in the original post. Also, the user name for your outgoing server should be your full email address as well, i.e "username@hotmail.com" or "username@live.com". I use both of these and have no issues. Hope this helps.
All the settings are the same and seem to work except the remove after download pop setting.

---

### Post by Paresh on 2009-05-19
> **RubBA said:**
> I've got another problem.
all settings seem to work i can receive and send mail but evolution keeps on making copies of al my mails. Wich resulted in a mailbox with 10.000+ e-mails.

I also had this problem, but only the first time after I set up the account, all mail that was downloaded by hotway (and left on server) was downloaded again.  However, once that was done, there were no further problems, even with leaving the mail on the server.

A possible 'solution' might be to delete the hotmail account, then delete all hotmail messages from your machine, then re-enter the hotmail account.  you will have to wait for them all to download again, but once the initial download is finished, there should be no further problems, at least that is how it worked for me.  Needless to say, ensure you have copies of important emails somewhere else before you try this.

---

### Post by crjackson on 2009-05-19
> **dwouters said:**
> Make sure your smtp.live.com encryption is set to TLS encryption. Any other setting, the server will reject. Double check and make sure the setting are exactly as in the original post. Also, the user name for your outgoing server should be your full email address as well, i.e "username@hotmail.com" or "username@live.com". I use both of these and have no issues. Hope this helps.

Yeah, that's EXACTLY how I have it. I have the same issue when using gmail pop/smtp as well. I think it must have something to do with Roadrunner.

---

### Post by crjackson on 2009-05-19
> **RubBA said:**
> Yeh thats right i did uncheck the box wich says delete the messages from server after downloading. I did that because i want to be able to read my mail from other workstations too, or is that also possible when i do check that box?  Still its strange, the mail client should know when a certain message has already been downloaded and skip them, even if they are stil on the server, not?

I MOSTLY use thunderbird and it does remember as you state. I haven't tried it that way with EVO so I don't know for sure.

---

### Post by cj13579 on 2009-05-20
> **Paresh said:**
> Now that pop3 is available FOC from Hotmail, you can amend your evolution account:-

Receiving email
Server Type = POP
Server = pop3.live.com
Secure Connection = SSL encryption

Sending email
Server Type = SMTP
Server = smtp.live.com
Secure Connection = TLS encryption

All other settings stay the same.

Not sure why TLS works for sending and SSL for receiving, but this is what worked for me.

The only thing is that it does seem to download all messages on the server, even if they were downloaded previously.

More info [here]("http://windowslivehelp.com/solutions/settings/archive/2009/01/06/send-and-receive-windows-live-hotmail-emails-from-a-mail-client.aspx")

Fantastic! Really simple - was having massive issues finding hotway on 9.04!

---

### Post by polauster on 2009-05-25
Ok I did all of the things you mentioned above and get my evolution working with hotmail but only works for receive messages but not for sending, does anybody have any idea about what to change or to do in order to get it working for all of the functions availables? I'll appreciate any direction, thanks!!

---

### Post by polauster on 2009-05-25
After a long while waiting it says connection timed ou, does anybody knows what to do regarding that?

---

### Post by Paresh on 2009-05-25
Make sure your sending encryption is set to TLS, and your login details are correct (username@hotmail.com)

---

### Post by rambo2914 on 2009-05-26
> **polauster said:**
> Ok I did all of the things you mentioned above and get my evolution working with hotmail but only works for receive messages but not for sending, does anybody have any idea about what to change or to do in order to get it working for all of the functions availables? I'll appreciate any direction, thanks!!

Hi, I have exactly the same problem! I am a new user of Ubuntu and I have configure Evolution with this topic but I can't send message... For receive messages it is ok....
Thanks to help us...

---

### Post by rambo2914 on 2009-05-26
Ok the problem is solved :

Receiving email
Server Type = POP
Server = pop3.live.com
Secure Connection = SSL encryption

Sending email
Server Type = SMTP
Server = smtp.live.com:587
Secure Connection = TLS encryption

---

### Post by RubBA on 2009-05-27
> **cj13579 said:**
> Fantastic! Really simple - was having massive issues finding hotway on 9.04!
Ok but if i dont check the box that says "leave messages on server" (wich is default not checked) will i still be able to pop from different computers?

---

### Post by Paresh on 2009-05-27
I usually check 'leave messages on server',
Presumably if this is not checked, messages will be deleted from the server once downloaded and thus would not be available for viewing on another computer.

---

### Post by Paresh on 2009-05-27
> **rambo2914 said:**
> Ok the problem is solved :

Sending email
Server Type = SMTP
Server = smtp.live.com:**587**
Secure Connection = TLS encryption

I didn't need to do that, but if it works for you, that's fine.  The default is port 25, but I guess that must be blocked by a firewall or something.

---

### Post by newbie09 on 2009-05-28
> **Siffle said:**
> I wish I could give more details but it simply says "error while Fetching Mail" at the bottom-left of the screen.  I enter my hotmail password and it just opens the enter password thing again.  Hotmail works fine in browser and on my other computer with Vista.  My administration password is the same as my hotmail password so it can be the only one to enter.

So I hit "send/receive" and I get:
The enter password screen that pops up for me is "Unable to connect to POP server pop3.live.com.  Error sending password - ERR authentication failed

I enter my hotmail/administrator password and it just pops up the same enter password again.  After I enter it a second time, it all goes away and just says the "error while Fetching Mail"

I'm stumped.  And yes, I've tried reentering the setting numerous times.



stiffle ... i was having the same problem tried this link ...

[http://linuxowns.wordpress.com/2009/03/04/setting-up-evolution-mail-gmail-and-hotmail/](http://linuxowns.wordpress.com/2009/03/04/setting-up-evolution-mail-gmail-and-hotmail/)

only receive works still unable to send

---

### Post by RubBA on 2009-05-28
> **Paresh said:**
> I usually check 'leave messages on server',
Presumably if this is not checked, messages will be deleted from the server once downloaded and thus would not be available for viewing on another computer.
ok well thats my theorie too. but when i do input exactly all the settings and check the box leave messages on server i keep on getting duplicates of every e-mail. But not everytime i check for new mail. Its at random times.  I'm going to give it a shot with thunderbird just to know for sure if its the mail client that gives the problems.

---

### Post by cj13579 on 2009-05-28
> **RubBA said:**
> ok well thats my theorie too. but when i do input exactly all the settings and check the box leave messages on server i keep on getting duplicates of every e-mail. But not everytime i check for new mail. Its at random times.  I'm going to give it a shot with thunderbird just to know for sure if its the mail client that gives the problems.

I had the random duplicate message retrieval aswell. I think that it is Evolution as didn't have the same problem in Thunderbird and all works fine.

---

### Post by cj13579 on 2009-05-28
> **Paresh said:**
> I usually check 'leave messages on server',
Presumably if this is not checked, messages will be deleted from the server once downloaded and thus would not be available for viewing on another computer.

If you don't check the box the messages **will be **removed from the server. This means that you won't be able to use a mail client on another computer, or if you are using a mail service like hotmail, be able to access you mail via the website either.

---

### Post by RubBA on 2009-05-28
> **cj13579 said:**
> I had the random duplicate message retrieval aswell. I think that it is Evolution as didn't have the same problem in Thunderbird and all works fine.
Yes indeed. Thunderbird works flawless here. Another thing i just found out through an error message from thunderbird is that the hotmail pop servers only allow a connection once every 15 minutes. Evolution never gave an error message indicating that so maybe thats where it goes wrong when it forces a connection? Or not... :P  But there must be some explanation...

---

### Post by cj13579 on 2009-06-15
I may have found a work around to using Hotmail with evolution and not getting it to download you whole inbox every time it checks for new mail.

In the settings for your hotmail account:  Edit > Preferences > Mail accounts.

Select the "Receiving Options" tab and uncheck the check for mail automatically tick box. Whenever you want to check for new mail just use the send/receive button on the toolbar.

I have been using this for a couple of weeks so far and have had no problems. 

Although HTML mail (especially with images) sometimes don't display properly I much prefer Evolution over Thunderbird because of the Calender and Tasks functionality. If someone finds something which allows automatic checking and doesn't download the whole box again then that would be even better. I have heard a rumour that if you set it to 15mins between checks then it is ok but I dont want to try for the hassle it causes if its wrong.

---

### Post by gleble on 2009-07-02
I have no bother receiving email but sending gives 'Could not connect to smtp.live.com' It doesn't mater which port I use the response is the same. Should I be attaching evolution to a particular port, if so how?

---

### Post by bertles86 on 2009-07-11
I'm having trouble receiving or sending! using a hotmail.com account on 9.04 and Evolution, with all the right settings! Any ideas?

---

### Post by cj13579 on 2009-07-13
> **bertles86 said:**
> I'm having trouble receiving or sending! using a hotmail.com account on 9.04 and Evolution, with all the right settings! Any ideas?

Ok, when you first clicked send/receive or when you first entered Evo after setting up the account did you get the box asking for your password? What exactly does the error message say when you try to send/receive?

In another direction have you checked your firewall and made sure evolution or the port it uses aren't blocked for some strange reason?

---

### Post by pavlovscat on 2009-07-14
Incoming server: pop3.live.com:995
 Username: your_username @hotmail.com
Use secure connection: SSL
Authentication type: password
 

Outgoing server: smtp.live.com:587
Server requires authentication: yes
Security: TLS
Authentication type: plain
 

I know you said you used the correct settings, but was not sure you had set the Authentication type to Plain under the outgoing server.
As far as I can tell, the incoming port specification is optional at this point, but is the recommended port from live.


Hope this works for you!

---

### Post by gleble on 2009-07-20
I am using Evolution with pop3.live.com and have tried it with pop3.live.com:995 but it's not working. Until this morning it was working now it's not. Any ideas

---

### Post by cj13579 on 2009-07-20
> **gleble said:**
> I am using Evolution with pop3.live.com and have tried it with pop3.live.com:995 but it's not working. Until this morning it was working now it's not. Any ideas

Are you running anything else that may be using those ports?

---

### Post by Evontroy on 2009-10-24
> **Paresh said:**
> Now that pop3 is available FOC from Hotmail, you can amend your evolution account:-

Receiving email
Server Type = POP
Server = pop3.live.com
Secure Connection = SSL encryption

Sending email
Server Type = SMTP
Server = smtp.live.com
Secure Connection = TLS encryption

All other settings stay the same.

Not sure why TLS works for sending and SSL for receiving, but this is what worked for me.

The only thing is that it does seem to download all messages on the server, even if they were downloaded previously.

More info [here]("http://windowslivehelp.com/solutions/settings/archive/2009/01/06/send-and-receive-windows-live-hotmail-emails-from-a-mail-client.aspx")


Thanks for the guide. I'm currently using Evolution now over Thunderbird!

---

### Post by ruth willis on 2009-10-26
I am having trouble getting evolution to send & receive , my server is POP3 pop.orangehome.co.uk and email is an @wanadoo.co.uk address, maybe i,ve filed in the wrong fields in preferences.can anyone Help?
Cheers Ruth:confused::KS

---

### Post by ~Niebr~ on 2009-11-04
i used the settings in the beginning with evolution, i can recieve, but i cant send, any help with this ?

---

### Post by cj13579 on 2009-11-05
> **ruth willis said:**
> I am having trouble getting evolution to send & receive , my server is POP3 pop.orangehome.co.uk and email is an @wanadoo.co.uk address, maybe i,ve filed in the wrong fields in preferences.can anyone Help?
Cheers Ruth:confused::KS

Hi Ruth,

What settings have you entered? And what errors are you getting? Are you able to connect to the server but are having authorisation issues or are you not able to connect to the server at all?

---

### Post by cj13579 on 2009-11-05
> **~Niebr~ said:**
> i used the settings in the beginning with evolution, i can recieve, but i cant send, any help with this ?

Check on your router to make sure that port 25 isn't being blocked on outbount traffic for any reason. Also, make sure that you are using TLS encryption.

---

