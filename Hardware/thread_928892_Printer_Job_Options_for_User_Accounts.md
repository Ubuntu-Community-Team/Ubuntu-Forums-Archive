---
title: "Printer Job Options for User Accounts"
date: 2008-09-24
forum: Hardware
---

### Post by gusmarshall on 2008-09-24
I have a Sharp MX-3501N set up in the office, where we are using "User Numbers" for print job accounting.  We have selected "Disable Printing by Invalid Users" on the printer control panel.  On a Windows machine, the print driver provides a tab for "Job Handling" where we can specify the "User Number."  The Linux CUPS driver, downloaded directly from Sharp, does not offer this Job Option by default.  I was wondering if anyone knew how to add it manually under "Other Options (Advanced)." I have tried "User," "User Number," "UserNumber," "user_number," "uid," "UserName" and the upper/lower-case versions of all of these, but to no avail.  Any ideas?  Successes?

We also have a Sharp MX-M350N for which I am having the same problem.

Thanks in advance!!
Cheers,
Gus

---

### Post by nipquad on 2009-05-29
I have the exact same issue.  Did you ever find a solution to this problem?

---

### Post by jvantslot on 2009-06-19
I too suffer from this issue.  Anybody have the correct option for user number?

---

### Post by niallb on 2009-07-24
I have both an MX-3500N and an MX-2700N and share your pain.

I've been having another run at getting it solved, and have purchased
the postscript module for one of the printers, and installed the supplied PPD driver on a windows machine here. 
I've just raised a query with Sharp as to how to print with user numbers using their provided PPD driver. Any forthcoming solution should be applicable to cups.

Let me know if any of you have gotten any further, and I'll post up my own progress as it happens.

NiallB

---

### Post by eric71 on 2009-09-04
I have this same issue in my office. I haven't got it working yet, but I found this blog that at least might point us in the right direction:

[http://apathy.jtsage.com/sharp-mx-4501n-on-ubuntu-linux](http://apathy.jtsage.com/sharp-mx-4501n-on-ubuntu-linux)

---

### Post by niallb on 2009-09-04
Sharp UK stated a week AFTER I purchased the postscript card that it was not possible to print with PPD driver with user PINs turned on. With PINs turned off, I could have printed to it without the card anyway, and the card is permanently tied to the printer, so not exactly something you can return. I'm waiting for our agent to come back to me with anything further, but looks like I made an unnecessary and very expensive purchase with the card. At the moment, I've turned PINs off on one copier, and put it in an area which is reasonably secure - not ideal, but functional.

Thanks for the pointer to the blog, I've tried that approach among many others, but I'll go at it with a fresh enthusiasm now that there's a hint somebody got it working!

---

### Post by eric71 on 2009-09-04
I also came accross this similar information for another Sharp printer, but still no luck with our office MX-3501N. Must be getting close...

[http://article.gmane.org/gmane.comp.printing.cups.general/20509](http://article.gmane.org/gmane.comp.printing.cups.general/20509)

---

### Post by nipquad on 2009-11-03
[I]Today, I finally figured out how to make my ubuntu laptop print to a Sharp MX-4501N workgroup copier. It was hell.

Basically, you need to get the .ppd from sharp - that part is easy. Then, if like my office, yours bases everything off of the 'user number' in the windows, you'll need to add this little bit to the .ppd before install. I put it right before all of the %== constraints lists and options.

*% **** Account number
*JCLOpenUI *JCLMXaccount/numero: PickOne
*OrderDependency: 80 JCLSetup *JCLMXaccount
*DefaultJCLMXaccount: A#####
*JCLMXaccount A#####/#####: "@PJL SET ACCOUNTNUMBER=<22>#####<22><0A>"
*JCLCloseUI: *JCLMXaccount
Make ##### your user number. You can probably change numero to number, but, I pulled this off of a spanish site, it works, and I'd prefer not to mess with it.[/I]

This works for me!  I pulled the PPD file for our MX-4501N and added the code at the bottom.  I replaced the #### with my UserID and it prints without issue.  I am using the same User ID that you would put in under the Job Handling menu within Windows.  Also, make sure to replace all the #### with the same number.  FYI the option will now be listed as "JCL" at the bottom of the Printer Options properties within Ubuntu and have your user number selected as an option.

Credit goes to eric71 for posting the original blog link that has these instructions

---

### Post by prusswan on 2013-01-04
> **nipquad said:**
> [I]Today, I finally figured out how to make my ubuntu laptop print to a Sharp MX-4501N workgroup copier. It was hell.

Basically, you need to get the .ppd from sharp - that part is easy. Then, if like my office, yours bases everything off of the 'user number' in the windows, you'll need to add this little bit to the .ppd before install. I put it right before all of the %== constraints lists and options.

*% **** Account number
*JCLOpenUI *JCLMXaccount/numero: PickOne
*OrderDependency: 80 JCLSetup *JCLMXaccount
*DefaultJCLMXaccount: A#####
*JCLMXaccount A#####/#####: "@PJL SET ACCOUNTNUMBER=<22>#####<22><0A>"
*JCLCloseUI: *JCLMXaccount
Make ##### your user number. You can probably change numero to number, but, I pulled this off of a spanish site, it works, and I'd prefer not to mess with it.[/I]

This works for me!  I pulled the PPD file for our MX-4501N and added the code at the bottom.  I replaced the #### with my UserID and it prints without issue.  I am using the same User ID that you would put in under the Job Handling menu within Windows.  Also, make sure to replace all the #### with the same number.  FYI the option will now be listed as "JCL" at the bottom of the Printer Options properties within Ubuntu and have your user number selected as an option.

Credit goes to eric71 for posting the original blog link that has these instructions


Incredible, I was able to print from our network printer (a Canon iR-ADV C2020) that is expecting a department id and pin, with no way to configure those. Your method worked perfectly (after digging out the correct ppd file from the rpm driver package and adding the snippet)

---

### Post by bethe on 2013-07-05
> **nipquad said:**
> [I]Today, I finally figured out how to make my ubuntu laptop print to a Sharp MX-4501N workgroup copier. It was hell.

Basically, you need to get the .ppd from sharp - that part is easy. Then, if like my office, yours bases everything off of the 'user number' in the windows, you'll need to add this little bit to the .ppd before install. I put it right before all of the %== constraints lists and options.

*% **** Account number
*JCLOpenUI *JCLMXaccount/numero: PickOne
*OrderDependency: 80 JCLSetup *JCLMXaccount
*DefaultJCLMXaccount: A#####
*JCLMXaccount A#####/#####: "@PJL SET ACCOUNTNUMBER=<22>#####<22><0A>"
*JCLCloseUI: *JCLMXaccount
Make ##### your user number. You can probably change numero to number, but, I pulled this off of a spanish site, it works, and I'd prefer not to mess with it.[/I]

This works for me!  I pulled the PPD file for our MX-4501N and added the code at the bottom.  I replaced the #### with my UserID and it prints without issue.  I am using the same User ID that you would put in under the Job Handling menu within Windows.  Also, make sure to replace all the #### with the same number.  FYI the option will now be listed as "JCL" at the bottom of the Printer Options properties within Ubuntu and have your user number selected as an option.

Credit goes to eric71 for posting the original blog link that has these instructions

It also worked for me. Thanks.

---

