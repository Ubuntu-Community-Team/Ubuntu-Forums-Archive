---
title: "Trying to go paperless..."
date: 2008-08-26
forum: General Help
---

### Post by hambone79 on 2008-08-26
I'm in the process of cleaning out all of my old notes and documents to free up some room in my apartment. I am doing this by scanning the notes into my Kubuntu box and saving them in PDF format. 

When I get done with all of the scanning I would like to setup some sort of server to create a searchable index of the PDF files. I will need some sort of software that has OCR (Optical Character Recognition) and will store the results in a SQL database.

Does anyone know of software that will allow me to do this

---

### Post by rax_m on 2008-08-27
I know of a full-blown application called KnowledgeTree that do that with a plugin. However, it may be overkill for home use as it is  a complete document management system. 

Otherwise, you may have to find a command line OCR app and script it to write the indexed files to a database.

---

### Post by rax_m on 2008-08-27
gocr is an example of a CLI OCR reader.

---

### Post by hambone79 on 2008-08-27
Knowledge tree looks like a nice piece of software, but I see a few problems with it:

1. The community version doesn't come with the Document scanning tool that supports OCR.
2. It seems to be geared more towards Windows than Linux.

I could probably put together some perl/php scripts that would use a command line tool, but I just don't have time to mess with it right now. Any other tools that you know of?

---

### Post by thedagger83 on 2008-08-27
Here's an idea:
1.Make the pdfs publically available on a webserver. 
2. Create a sitemap and submit it to google so that it will crawl (and cache) it.
3. Wait... 
4. Use google to search your PDFs, and you'll have a remote backup ;)

---

### Post by mssever on 2008-08-27
> **thedagger83 said:**
> Here's an idea:
1.Make the pdfs publically available on a webserver. 
2. Create a sitemap and submit it to google so that it will crawl (and cache) it.
3. Wait... 
4. Use google to search your PDFs, and you'll have a remote backup ;)
Now there's some creative thinking :)

If course, if the documents contain sensitive information, this isn't such a good idea for those documents.

---

### Post by unutbu on 2008-08-27
Perhaps this is useful?
[http://ubuntuforums.org/showthread.php?t=882899](http://ubuntuforums.org/showthread.php?t=882899)

---

### Post by hambone79 on 2008-08-28
> **unutbu said:**
> Perhaps this is useful?
[http://ubuntuforums.org/showthread.php?t=882899](http://ubuntuforums.org/showthread.php?t=882899)

That's a good start, but I'm still pressed for time so I don't have time to develop the user interface. I think I'm going to go with OpenKM ([http://www.openkm.com/](http://www.openkm.com/)) because it has all the features I want and seems to be a fairly mature project.

---

