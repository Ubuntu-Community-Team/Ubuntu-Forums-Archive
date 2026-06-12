---
title: "Alternative justvoip ubuntu linux"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by miros84 on 2008-12-24
Hello everybody. The program justvoip for windows, I used to talk for free calls to landlines, does not exist for ubuntu. I tried to install it with wine, but it's impossible. Somebody knows any alternatives or how to install this program on ubuntu?

---

### Post by ToasterThief on 2008-12-24
Try out [Ekiga]("http://wiki.ekiga.org/index.php/Main_Page")

---

### Post by namdung on 2008-12-24
There seems to be a version for MAC and Linux but one needs to register.

[http://www.justvoip.com/en/download.html](http://www.justvoip.com/en/download.html)

Good luck!!!

---

### Post by miros84 on 2008-12-27
This link just let me enter en the contro panel inside the site, but I cannot call from there. And about ekiga? Seems to be very different of just voip. And I don't know the price if it's good.

---

### Post by ToasterThief on 2009-01-02
> **miros84 said:**
>  And about ekiga? Seems to be very different of just voip. And I don't know the price if it's good.

Yes, it's a bit more than just VoIP, so what?
Price? It's free and Open Source.

---

### Post by Gusss on 2009-03-29
> **ToasterThief said:**
> Yes, it's a bit more than just VoIP, so what?
Price? It's free and Open Source.

I think he means the price of the calls - you can call mainy countries landlines free with Justvoip potentially saving a lot of money if you have relatives abroad. I m not sure Ekiga offers this . Also the link to Justvoip for Linux just takes you to the windows installation page. 
I would also be interested in anyone who could tell us how to make free calls to landlines using Linux as I prefer using Linux whenever possible and windows has messed up my soundcard !

---

### Post by larsbjo on 2009-04-14
If you create a username at the JustVoip site, and pay a minimum 10 Euro up front, you can make calls "phone-to-phone". Phone-to-phone is brilliant as it offers good quality connections also for people with limited bandwidth. Calls are also very cheap. 
I can call from Brazil to Europe for as long as I like by only paying a 5.ct (Euro) connection fee.

It would be great if anyone could make the Windows app work under Wine. The JustVoip web-interface sucks. It have a much to short timeout and no phone-book option. It also hangs in Firefox when trying to log in after a timeout. It seems to work better in Opera.

---

### Post by miros84 on 2009-08-05
I got it.
I installed twinkle and I added my justvoip acount and now I can call free, using my justvoip acount by twinkle.

---

### Post by arjmage on 2009-09-01
You don't need a linux version for justvoip. The betamax servers are accessible on SIP connections, and there's a host of (free) SIP clients on linux. Ubuntu comes installed with the Ekiga softphone that supports this protocol. You just need to configure the settings correctly.

From [http://www.justvoip.com/en/sipp.html](http://www.justvoip.com/en/sipp.html)

    ```
SIP port : 5060
    Registrar : sip.justvoip.com
    Proxy server : sip.justvoip.com
    Outbound proxy server : leave empty
    Account name : your JustVoip username
    Password : your JustVoip password
    Display name/number : your JustVoip username or voipnumber
    Stunserver (option) : stun.justvoip.com
```

In my jaunty's ekiga, I don't need to enter any port. Just a display username, and then the justvoip username and password for authentication directed at the above registrar.

To make a call, you enter a number after the "sip:" in the software, and (if the justvoip account in registered in the software) the call will go through straightaway via your justvoip account. Nifty!

However, I could not retrieve my address book from justvoip. Any ideas on how to do this from the internet login page?

---

### Post by miros84 on 2009-12-25
I have found out alternativity of justvoip.
That is Twinkle.
Is a debian and ubuntu package.
It work perfect with justvoip.

---

### Post by Benito Lopera on 2010-05-27
> **miros84 said:**
> I have found out alternativity of justvoip.
That is Twinkle.
Is a debian and ubuntu package.
It work perfect with justvoip.

Hello Miros, hello everybody. I´m interested too in using Justvoip with Twinkle but I can´t set it up correctly, it always shows an error message (505 I think). Could you please tell me how you configure the setup wizard?. Thank you

---

### Post by Raeesi on 2010-09-29
Hi all

I tried several times with twinkle and ekiga but no luck!

my settings in twinkle are:

[IMG]http://img3.imageshack.us/img3/2927/screenshottwinkleuserpr.png[/IMG]



[IMG]http://img829.imageshack.us/img829/2927/screenshottwinkleuserpr.png[/IMG]

---

### Post by Stefano G on 2011-06-13
hi guys,

thanks for the informations.
I used Twinkle too, and calls are fine, but i can't see the status of my credit or cost information of the calls, and even don't know how can i get my phonebook from XP version of justvoip.

any one got a solution?

thanks in advance

stefano

---

