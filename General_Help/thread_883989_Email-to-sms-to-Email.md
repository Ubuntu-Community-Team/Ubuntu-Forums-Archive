---
title: "Email-to-sms-to-Email"
date: 2008-08-08
forum: General Help
---

### Post by starstorm1 on 2008-08-08
I am looking for software that can do this:

A. E-mail to sms
1. Receive e-mail
2. Covert the e-mail text into an SMS and send it via voip provider
to my mobile phone.

B. SMS to e-mal
1. Receive my sms
2. Convert sms to e-mail and send via my SMTP server to e-mail recipient.


Is there anything out there that can do A or B or both?

 I know that some mobile providers have this  feature built into their phone services but I don't want to use that.

Thanks!

---

### Post by brian_p on 2008-08-08
> **starstorm1 said:**
> 

Is there anything out there that can do A or B or both?



A can be implemented with smssend and shell scripting.

---

### Post by Nick Lake on 2008-08-08
You could also just get a GSM Modem and send AT commands to it for SMS. You can read the inbox off the SIM card via AT+CMGL="REC UNREAD".

---

### Post by Viridia on 2008-08-08
Just a gmail account should be able to do that. Say your email address is [email]abc@gmail.com[/email]. Set up a filter that forwards all e-mail to [email]abc@gmail.com[/email] to your phone e-mail address. I'm not sure about other carriers, but if you use Verizon, you would forward it to (your phone number)@vtext.com

Google around for other service providers

---

