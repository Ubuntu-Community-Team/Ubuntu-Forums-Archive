---
title: "Document Management Systems"
date: 2008-11-26
forum: General Help
---

### Post by artesvida on 2008-11-26
I'm in the market for an enterprise document management system.  A selection committee has evaluated a handful of systems, and wants to move forward on a particular commercial product.  However, we didn't really look at open source options, and I feel we should consider those before moving forward.

Googling "document management open source" reveals a few contenders, including (but not necessarily limited to):
[LIST]
[*]Alfresco
[*]KnowledgeTree
[*]OpenKM
[*]Epiware
[*]xinco
[/LIST]

I would like some feedback on any of these (or other open source) systems.  Specifically from users who have implemented and are currently using one of these systems in a small to medium sized business setting.  I see that most of these systems have a "community" (open source) edition, and one or more "professional" ($) editions.  We're comfortable springing for the "pro" edition, but I'd like to hear any info you have about the limitations/benefits/drawbacks of sticking with or going beyond the open source version.

Our requirements, in a nutshell:
[LIST=1]
[*]**Ease of use** - we recognize that people will be resistant to change, so this system must be very easy to use.
[*]**Integration with Windows and Microsoft Office 2007** - sorry to say this is our standard right now, and the system must play well with it.
[*]**Full text search **on PDF, Word, Excel, and PowerPoint documents.
[*]**OCR** either included or available as an add-on.
[*]**Versioning**, with a check-out/check-in process.
[*]**Workflow** - so that people can route documents
[*]**Scalability** - this system will probably grow to an enormous size.  Although we probably won't have more than 50 concurrent users.
[*]**Comprehensive e-mail archiving **(we won't implement this today, but probably in the future)
[/LIST]

Another consideration is that we are also looking to implement a corporate intranet, and (apparently) some of these DMS systems are considered CMS systems as well.  So, we might want to use this DMS for our intranet.

Thank you!!!

---

### Post by FrankSpierings on 2008-11-27
Artesvida,

Since I've been looking into it recently, I can tell you the following.

- OpenKM is definitely not what **you** are looking for, since it doesn't contain workflow management. OpenKM is more qualified as a knowledge management system (..KM). It is easy to use though.

- Alfresco is more like MS SharePoint, although I found it (community edition) quite difficult to setup within an existing environment. No real problems if you want to use the build-in tomcat server though. I believe it should scale very well, but obviously haven't tested this.

Hope this info gets you on your way a bit.

Frank Spierings

---

