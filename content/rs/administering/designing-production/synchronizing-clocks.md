---
Title: Synchronizing cluster node clocks
description: 
weight: $weight
alwaysopen: false
---
It is important to ensure all cluster node's clocks are synchronized
using Chrony and/or NTP. Without this synchronization, there may be
problems with internal cluster communications and have downstream
impacts.

When you initially install Redis Enterprise Software, the install script
asks for permission to configure a scheduled Cron job if it does not
detect Chrony or NTP. This should ensure the node's clock is always
synchronized. If you did not confirm configuring this job during the
installation process, you must use the Network Time Protocol (NTP)
regularly to ensure that all server clocks are synchronized.

To synchronize the server clock, run the command relevant to your host's
operating system. For example, in Ubuntu, the following command can be
used to synchronize a server's clock to an NTP server:

``` {style="border: 2px solid #ddd; background-color: #333; color: #fff; padding: 10px; -webkit-font-smoothing: auto;"}
$ sudo /etc/network/if-up.d/ntpdate
```

If you are using Geo-Replication, it is critical to keep OS clocks
consistent across clusters as well. Certain aspects of conflict
resolution are achieved using OS time. For specific information, please
see [Network Time
Services]({{< relref "/rs/administering/intercluster-replication/crdbs.md#network-time" >}})
as they pertain to CRDBs.