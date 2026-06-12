---
title: "Apache2 envvars reset/example file"
date: 2008-09-13
forum: General Help
---

### Post by open4life on 2008-09-13
After updating my ubuntu (desktop) install for the first time in months, my virtual hosts stopped working. When restarting apache I get an error saying:
```
ERROR: APACHE_PID_FILE needs to be defined in /etc/apache2/envvars
```
When opening the file I can see that it only contains:
```
# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
#
# envvars-std - default environment variables for apachectl
#
# This file is generated from envvars-std.in
```
It seems that the file contains only comment lines. Where can I find an example file or generate a new one? I tried reinstalling apache but it didn't work.

I use apache2 on ubuntu 8.04.

This is quite urgent, so if someone could post a working envvars file I would be very happy.

---

### Post by open4life on 2008-09-13
I've found a working envvars file, but now I can't get my virtual hosts running. No errors on apache restart, and sites-enabled folder is imported in apache config file.

---

### Post by open4life on 2008-09-13
Problem solved, was an error in one of the virtual host files. Dunno why it worked before though :P

---

### Post by Bright on 2008-09-13
Hi, I am expieriencing the same issue after upgrading to ubuntu 8.04. Can you please specify the error in your virtual hosts file so that I may check that as well?

Thanks

---

### Post by Bright on 2008-09-13
My issue ended up being the "DocumentIndex" line. I knew it was line 7 as when trying to start apache2 i was told so but it didnt occur to me that the entire line needed commenting out... so I had spent an hour playing with syntax etc... LMAO

Anyway, for those with the same issue just comment out the "DocumentIndex" line.

---

