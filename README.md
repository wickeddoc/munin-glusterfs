munin-glusterfs
===============

Munin GlusterFS plugin for glusterfs 3.2+

This plugin can graph:
 - Open and maximum fd count
 - Read performance per brick
 - Write performance per brick

Intially written by Bernd Weber (https://github.com/berndmweber)
 
---------------------
 Examples
 Create a symbolic link to glusterfs_<volume>_<open|readperf|writeperf>
       ln -s /usr/share/munin/plugins/glusterfs_ /etc/munin/plugins/glusterfs_shared_open
           graph open calls for all bricks of the 'shared' volume

       ln -s /usr/share/munin/plugins/glusterfs_ /etc/munin/plugins/glusterfs_shared_writeperf
           graph write performance for all bricks of the 'shared' volume

---------------------

 Add the following to your /etc/munin/plugin-conf.d/munin-node:

       [glusterfs_*]
       user root                   # Mandatory
       env.blocksize <blocksize>   # Optional
       env.blockcount <blockcount> # Optional

 If you want to monitor a specific brick per volume you'll have to add an additional
 section for each brick per volume in your config file
       [glusterfs_<volume>_*]
       env.brick <brick_name>
       env.share <share_export_path>

---------------------

Log
Revision 0.2  04/27/2015
 -Added support if you want to monitor more than one volume on the same host

Revision 0.1  01/31/2013
 -First version of the GlusterFS Munin plugin
