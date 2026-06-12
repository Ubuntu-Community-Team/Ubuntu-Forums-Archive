---
title: "[SOLVED] Automatically Shutdown on Process End"
date: 2008-07-19
forum: General Help
---

### Post by ashmew2 on 2008-07-19
Hello People .

I host a Counter Strike 1.6 Server on my home machine. The server is set up fine and people are playing in the server. I just want to know if its possible to shutdown the system as soon as the server is shutdown.

I have given admin privileges to a friend who will shut down the server as soon as they are done playing. I want the system to be shut down as soon as the server is killed.

Thanks.

---

### Post by sdennie on 2008-07-19
You should be able to do that without a problem.  One way to do it would be to make a simple script for the server and start it with sudo.  Something like this:

```

#!/bin/bash

su name_of_cs_server_user -c "command_to_start_server"
shutdown -h now

```

If you run that script with sudo, it should run the server as name_of_cs_server_user and it should shutdown the machine as soon as the server ends.

---

### Post by ashmew2 on 2008-08-24
Thank You.

---

