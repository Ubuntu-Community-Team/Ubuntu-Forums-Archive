---
title: "using signature pad - serial port connected with MS Terminal Server 2003"
date: 2010-10-25
forum: Hardware
---

### Post by nate1974 on 2010-10-25
I'm trying to get a serial port connected signature pad to redirect when logging into a MS Terminal Server 2003 session so customers can sign documents. I'm using Ubuntu 10.10 and the included Terminal Server Client. I've edited the settings for the connection to include:
redirectcomports:i:1
When I login to the server and start the application it appears that the application thinks it can access the redirected serial port but nothing happens onscreen when I sign the document and the application pops an error when I go to save because it has no signature registered for the client.
Any ideas would be most appreciated.
Thanks,

---

