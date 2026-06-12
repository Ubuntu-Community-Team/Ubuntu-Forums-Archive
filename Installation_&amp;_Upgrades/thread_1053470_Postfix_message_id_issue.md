---
title: "Postfix message id issue"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by micro_user on 2009-01-28
Hi,

I have an ubuntu server with Postfix & Dovecot configured for email system. I can send and receive emails.
When an email is received in outlook the following details are also added with the email

Message-Id: <20090128233629.46B033002433F@myservername>
Date: Thu, 29 Jan 2009 10:36:29 +1100 (EST)
Return-Path: www-data@myservername
X-OriginalArrivalTime: 28 Jan 2009 23:36:14.0537 (UTC) FILETIME=[3593DB90:01C981A1]


How do I get rid of this extra fields

Thanks

---

### Post by micro_user on 2009-01-28
Hi,

Also to add to this, when the message is received in outlook, the sent section reads None, whereas it should display the time and date when the message was received. Is it something to do with Dovecot conf file or php conf?

Also, the email script which sends email works well without any additonal information on other hosting provider network. Its my network where the email received brings up the additional information.

Thanks

---

### Post by mspIggy on 2009-03-04
i have this same issue and infact due to user apache 'www-data' coming up in Return-Path: www-data@myservername - every single email to AOL, verizon, comcast, yahoo and others never arrive - hotmail winds up in junk folder...

how do we get rid on this and insert the site that is sending?

this happens with php scripts using mail()

i have tried everything in adding From and just about every detail i can think of to header

including:

```
     
	$headers  = "MIME-Version: 1.0\r\n";
	$headers .= "email = <$vend_email>\r\n";
	$headers .= "From: <$vend_email>\r\n";
	$headers .= "Content-type: text/plain; charset=iso8859-1\r\n";
	// $headers  = "additional headers\r\n";
	$return_path = "Return Path $vend_email\r\n";  // Return path for errors
    $headers .= "ReplyTo: $vend_email\r\n";
   $headers .= "X-Priority: 1\r\n"; 
   $headers .= "X-MSMail-Priority: High\r\n";
    $headers .= "$vend_name <$vend_email> HTML-Mailer v1.0\r\n";
	 $headers  = "ini_set('sendmail_from', '$vend_email')";
```

and this damndable return path stays www-data....

---

### Post by mccork91 on 2010-01-13
Hi there,
 
Having exactly the same problem as described:
 
Using Ubuntu  and postfix
 
Its causing problems with customers thinking that the emails we send are spam
 
any help would be appreciated

---

