---
title: "ls command not working and offset terminal text ??"
date: 2008-11-04
forum: General Help
---

### Post by excetara2 on 2008-11-04
I ran and setup the Genesis Simulator (biological network simulator). All this entails is downloading running ./binsetup and copying a .simrc file into your home directory.

The genesis simulator runs perfectly. When I try to execute the ls command within the program, it won't work. On my Fedora machine it works fine. Also the commands become offset over from the left side. I will paste the example below. Anyone know how to fix this?

====================================

                                    Executable:         /usr/lib/genesis/genesis

--------------------------- Starting XODUS 2.0 ---------------------------

                                                                          The diskio library uses the netcdf-version 3.4 library, which is provided
                                                                   "as is" under the terms of distribution and usage by UCAR/Unidata.
                                                     Please see src/diskio/interface/netcdf/netcdf-3.4/copyright.html
                                     for the full notice.

                                                         The kinetics library is copylefted under the LGPL, see kinetics/COPYRIGHT.

                                                   Startup script:     .simrc
SIMPATH=. /home/jds/genesis-2.3/genesis/startup /home/jds/genesis-2.3/genesis/Scripts/neurokit /home/jds/genesis-2.3/genesis/Scripts/neurokit/prototypes
SIMPATH=. /home/jds/genesis-2.3/genesis/startup /home/jds/genesis-2.3/genesis/Scripts/neurokit /home/jds/genesis-2.3/genesis/Scripts/neurokit/prototypes /home/jds/genesis-2.3/genesis/Scripts/X1compat
SIMNOTES=/home/jds/.notes
GENESIS_HELP=/home/jds/genesis-2.3/genesis/Doc
genesis #0 > ls
unable to execute 'ls'
                      genesis #1 > 


Thanks in Advance

---

