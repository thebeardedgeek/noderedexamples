## Setting up Node-RED
Follow the steps found on this link: https://github.com/IBM/ibmi-oss-examples/tree/master/nodejs/node-red
I wrote a blog post to help you get started as well: https://ibmicommunity.thebeardedgeek.com/2020/07/setup-node-red-and-using-acs-http-proxy-on-ibm-i/

## Nodes needed from Palette to run this
 - Click the menu at the upper-right corner and click Manage palette
 - Click Install and type the name of the node that you wish to install

```
node-red-dashboard
node-red-contrib-db2-for-i
node-red-node-rbe 
node-red-node-tail
node-red-node-ui-list
node-red-node-ui-table
```

## Import this example
- Click the menu at the upper-right corner and click Import->Clipboard.
- Select the admindashboard.json file to import to current flow or select import to new flow.
- Setup the database connection
```
1. Double-click on the Local_DB node
2. Click on the pencil next to the Database field
3. Complete the form. Enter the Connection Name, User, Password, and Database = *LOCAL 
(this user can have restricted access to the system – I would recommend setting up a node user service account for this access)
4. Click Update
5. Click Done
6. Update all of the Local_DB nodes (or any other database nodes that you have with this new connection)
```
- Click the deploy button at the upper-right corner
- Visit http://yourip:1880/ui to see the dashboard

## Explanation of Dashboard
***All of these dashboard items are near real-time***
 - This dashboard contains different insights into the localhost IBM i system it is running on
 - The ***Work Problem Status*** section (upper-left) shows a green check mark when there are no issues in WRKPRB or a red x if a problem is detected
 - The ***ASP*** and ***Total CPU Usage*** shows the stats on the system
 - The ***Subsystems*** section shows all of the subsystems on the system. The arrows going both ways means that the SBS is running; the x means that it is not
 - The charts in the middle are pretty self explanatory. You can mouse over the graphs for more detailed info on the bars
 - The ***Scheduled Jobs for Current Day*** section (upper-right) shows the scheduled jobs from this point-in-time going forward; jobs that have yet to run
 - The ***Job Queues with Active Jobs*** section shows stats from QSYS2.JOB_QUEUE_INFO where ACTIVE_JOBS > 0
 - The ***Job Queues with Jobs Waiting*** section is what jobs would show in WRKJOBQ
 - The ***Disabled Users*** section shows you all of the users with the status of *DISABLED on their profile. I played around with this one to see what I could do and made it so that you can change the password and enable the user. This is just a proof-of-concept and I would add a lot more safe guards and logic around it before I would put it in production but I wanted to show what was possible. You can click the row, enter a password, hit OK --> and you will get a success message or an error message.

 I hope this helps everyone. Please give me some feedback and let me know what you think.

![screen shot](./dashboardscreenshot.png?raw=true)

![screen shot](./flowscreenshot.png?raw=true)
