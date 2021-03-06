# Administering Liferay Portal [](id=administering-liferay-portal)

You know how all these retailers want to advertise themselves as a "one stop shop" for whatever it is that you want? The idea is that they have so much stuff that chances are that whatever you're looking for is there. Liferay's control panel is something like this. If you want to create users, sites, organizations, configure permissions and plugins, and pretty much anything else, you'll do it with the control panel. The nice thing about the control panel is that it makes all this very easy to do. This chapter takes all the concepts you learned about Liferay in chapter 1 (sites, organizations, and more) and makes them concrete. Here, you'll learn how to create and manage every aspect of Liferay's configuration. 

This chapter covers the following activities:

-   Using the control panel to manage users, organizations, sites, user groups, roles, and teams

-   Using the control panel to manage password policies, authentication settings, mail host names, email notifications, display settings, and monitoring

-   Using the control panel to manage server administration, portal instances, plugins, and updates

Let's begin our examination of Liferay's control panel by looking at how to manage and organize users in Liferay Portal.

## Managing Users, User Groups, Organizations, Sites, Teams, and Roles [](id=managing-users-user-groups-organizations-sites-teams-and-roles)

The Portal section of the control panel is used for most administrative tasks. You'll find there an interface for the creation and maintenance of

- Users, User Groups, and Organizations

- Sites and Teams

- Site Templates

- Page Templates

- Roles

Additionally, you can configure many server settings, including:

- Password Policies

- Portal Settings

- Custom Fields

- Monitoring

- Plugins Configuration

You'll use the Portal section of the control panel to create your portal structure, implement security, and administer your users. Configurable portal settings include mail host names, email notifications, and authentication options including single sign-on and LDAP integration. Note that only users with the administrator role, which is a portal scoped role, have permission to view this section of the control panel. You can, of course, grant custom roles permissions to one or more sections.

### Adding users [](id=lp-6-1-ugen12-adding-users-0)

Let's add a user account for yourself and configure this account so that it has the same administrative access as the default administrator account. Go up to the Dockbar, mouse over *Go to* and click *Control Panel*. Then open the *Users and Organizations* page under the *Portal* category. Click the *Add* button and select *User*. Fill out the Add User form using your name and email address. When you are finished, click *Save*.

![Figure 12.1: The Add User Screen](../../images/01-add-user-screen.png)

After you submit the form, the page reloads with a message saying that the save was successful. An expanded form appears that allows you to fill out a lot more information about the user. You don't have to fill anything else out right now. Just note that when the user ID was created, a password was automatically generated and, if Liferay was correctly installed (see chapter 11), an email message with the password in it was sent to the user. This, of course, requires that Liferay can properly communicate with your SMTP mail server.

![Figure 12.2: Liferay's User Account Editor](../../images/01-user-account-editor.png)

If you haven't yet set up your mail server, you'll need to use this page to change the default password for the user ID to something you can remember. You can do this by clicking on the *Password* link in the box on the right, entering the new password in the two fields, and clicking *Save*. Next, you should give your user account the same administrative rights as the default administrator's account. This allows you to perform administrative tasks with your own ID instead of having to use the default ID. It also helps to make your portal more secure by deleting or disabling the default ID.

Click the *Roles* link. The control panel's Roles page shows the roles to which your ID is currently assigned. You should have one role: Power User. By default, all users are assigned the Power User role. You can give this role certain permissions if you wish or disable it altogether. You can also define the default roles a new user receives. We'll see how to do this later.

To make yourself an Administrator, click the *Select* link. A dialog box pops up with a list of all the roles in the system. Select the Administrator role from the list. The dialog box disappears and the role is added to the list of roles associated with your account. Next, click the *Save* button, which is at the bottom of the blue bar of links on the right. You are now an administrator of the portal. Log out of the portal and then log back in with your own user ID.

We'll next look at some aspects of user management. 

### User management [](id=lp-6-1-ugen12-user-management-0)

If you click the *Users* link on the left menu of the control panel, there are now two users in the list of users. If you want to change something about a particular user, you can click the *Actions* button next to that user.

**Edit User:** takes you back to the Edit User page, where you can modify anything about the user.

**Permissions:** allows you to define which roles have permissions to edit the user.

**Manage Pages:** allows you to edit the personal pages of a user.

**Impersonate User:** opens another browser window which allows you to browse the site as if you were the user.

**Deactivate:** deactivates the user's account.

Note that most users can't perform most of the above actions. In fact, most users won't even have access to this section of the control panel. You can perform all of the above functions because you have administrative access.

Let's look next at how to manage organizations. 

### Managing organizations [](id=lp-6-1-ugen12-managing-organizations-0)

Organizations are used to represent hierarchical structures such as those of companies, non-profit organizations, churches, schools, and clubs. They have been used to represent a sports league, with various sports (soccer, baseball, basketball, etc.) and their teams as sub-organizations. If you have a collection of users that fit into a hierarchical structure, you can model that as an organization.

Your portal design might not need organizations or it might have one or several, depending on your portal's function. For example, a simple photo-sharing web site could be powered by sites only (see below for information on sites). On the other hand, organizations are useful for corporations or educational institutions since their users can be placed easily into a hierarchical structure. In fact, organizations in Liferay are designed to model any group hierarchy, from those of government agencies all the way down to those of small clubs. Of course, your portal can use both organizations and independent sites. For example, a corporation or educational institution could create a social networking site open to all portal users, even ones from separate organizations. 

Organizations and suborganizations can be created in a hierarchy to unlimited levels, and users can be members of one or many organizations. These organizations can all reside in a single hierarchy or cut across different hierarchies. Note that the rights of an organization administrator apply both to his/her organization and to any child organizations. By default, members of child organizations are members of the parent organizations. This behavior can be customized in your portal's `portal-ext.properties` configuration file.

Additionally, Organizations can be associated with roles. One application of this in a corporate setting might be an IT Security group. You could have a suborganizaton of your IT organization that handles security for all of the applications company-wide. If you grant the IT Security organization the same administrator role you just gave to your own ID, all members of the organization would have administrative access to the portal. Suppose now that a user in this organization later was hired by the Human Resources department. The simple act of removing the user from the IT Security organization also removes the user's administrative privileges, since the privilege came from the IT Security group's role. By adding the user to the HR organization, any roles the HR organization has (such as access to a benefits system in the portal) are transferred to the user. In this manner, you can design your portal to correspond with your existing organization chart, and users' permissions are granted according to their positions in the chart.

Of course, this is only one way to design it. If you have more complex requirements, you can combine organizations with teams and scoped roles to assemble the sets of permissions you wish to grant to particular users. But we'll get to that. Let's first see how to manage organizations. 

To add an organization, click the *Users and Organizations* link on the left side of the control panel. Then click the *Add* button and choose *Regular Organization*. 

Does your organization need to have its own web site? Most organizations don't, but some do, and Liferay provides this ability by attaching a site to an organization. To attach a site when you create an organization, click the *Organization Site* tab at the right, and check the *Create Site* box. If you don't know right now if your organization needs a web site, that's fine: you can always add one later if the need arises. 

![Figure 12.3: Adding an organization](../../images/01-add-organization-screen.png)

**Name:** Enter a name for the organization.

**Type:** Choose whether this is a regular organization or a location. A location cannot have any suborganizations.

**Parent Organization:** Select an organization in the system to be the direct parent of the organization you are creating. Click the *Remove* button to remove the currently configured parent.

---

![tip](../../images/01-tip.png) **Tip:** Note that you're already a member of any organizations that you create. By creating an organization, you become both a member and receive the Organization Owner role, which gives you full rights to the organization. You can, of course, add other users to this role to make them Organization Owners. 

---

Fill out the information for your organization and click *Save*. As before with users, the form reappears and you can enter more information about the organization. Organizations can have multiple email addresses, postal addresses, web sites, and phone numbers associated with them. The Services link can be used to indicate the operating hours of the organization, if any.

For now, click the *Back* button. This takes you back to the list of organizations.

Click the *Actions* button next to the new organization you created. This shows the actions you can take to manipulate this organization.

**Edit:** lets you specify details about the organization, including addresses, phone numbers, email addresses, and websites.

**Manage Site:** lets you create and manage public and private pages for the organization's site.

**Assign Organization Roles:** lets you assign organization-scoped roles to users. By default, Organizations are created with three roles: Organization Administrator, Organization User, and Organization Owner. You can assign one or more of these roles to users in the organization. All members of the organization automatically get the Organization User role so this role is hidden when you click Assign Organization Roles.

**Assign Users:** lets you search and select users in the portal to be assigned to this organization as members.

**Add User:** adds a new user in the portal and assigns the user as a member of this organization.

**Add Regular Organization:** lets you add a child organization to this organization. This is how you create hierarchies of organizations with parent-child relationships.

**Add Location:** lets you add a child Location, which is a special type of organization that cannot have any children added to it.

**Delete:** deletes this organization from the portal. You must ensure that the organization has no users in it first.

If you click the *View* button at the top of the Users and Organizations page and select *View Hierarchy* you can view both a list of users who are members of this organization and a list of all the suborganizations of this organization.

We briefly mentioned sites during this discussion. Sites are another construct within the portal, and have different properties than organizations. Let's see how you can use them. 

### Sites [](id=lp-6-1-ugen12-sites-0)

As stated in chapter 1, a site is a set of pages that can be used to publish content or applications. Sites can be independent or they can be associated to one organization and act as the website of that organization.

Liferay's sites can be used for a variety of purposes, from corporate websites to company intranets including small sites to collaborate among members of a team. To support all types of collaboration and social scenarios, Liferay's sites support three types of membership types:

- Private: Users are not allowed to become members of the site. Site administrators can still manually select users and make them members of the site.
- Restricted: Users are allowed to request members of the site and site administrators have to aprove the request. The request can be done from the *My Sites* application.
- Open: Users are allowed to become members of the site at any time. This can be done from the *My Sites* portlet.

In addition to these memberships, when a site is associated to an organization, all the users of that organization are automatically considered members of the site.

Members of a site can be given additional privileges within the site by using Liferay's permission settings. It is also possible to assign different roles within the site to different members. This can be done through *site roles* which are defined equal for all sites or *teams* which are unique for each site.

Liferay's Sites can have two hierarchies of pages: public pages and private pages. A site can have only public pages, only private pages or both. The main difference between the two hierarchies is that private pages can only be accessed by members of the site. For both of them it is possible to restrict access to them in finer detail for each page through the permission system. Public pages and private pages are accessed through a different URL and can have a different look and feel, but they share the same content.

An example of using sites could be a corporate Intranet running Liferay which might have sites for all the organizations in the company: Sales, Marketing, Information Technology, Human Resources, and so on. But what about the corporate health and fitness center? That's something that everybody in the company, regardless of organization, may want to join. This makes it a good candidate for an open and independent site. Similarly, the home page for a corporate intranet should probably be placed in an open independent site so that any member of the portal can access it.

For other kinds of web sites, you may want to use independent sites to bring people together who share a common interest. If you were building a photo sharing web site out of Liferay, you might have independent sites based on the types of photos people want to share. For example, those who enjoy taking pictures of landscapes could join a Landscapes site, and those who enjoy taking pictures of sunsets could join a Sunsets site. 

Liferay always provides one default site, which is also known as the main site of the portal. This site does not have its own name, but rather takes the name of the portal. By default the portal name is *liferay.com*, but this value can be changed through the simple configuration of the setup wizard. The portal name can also be changed at any time through the control panel within *Portal Settings*.

---

![tip](../../images/01-tip.png) **Tip:** Prior to Liferay 6.1, there were two ways of creating sites: organizations and communities. This situation has been simplified to provide more ease of use and allow for more flexibility. The main role of organizations is still or organize the users of the portal in a hierarchy but they can also have associated sites. Communities can still be created through independent sites, but the new name reflects the fact that sites can be used for many different purposes besides communities.

---

Sites can be created through the control panel, like all administration operations in Liferay. To add a site, click the *Sites* link on the left side of the control panel in the Portal section, and then click *Add* in the toolbar. If there is at least one site template available, a dropdown menu will be shown allowing you to select a *Blank Site* or one of the site templates available. *Site templates* provide a preconfigured set of pages, applications and content that can be used as the basis of the site.

The following figure shows the form that needs to be filled when creating a *Blank Site*.


![Figure 12.4: Adding a Site](../../images/01-add-site-screen.png)

**Name:** is the name of the site you wish to create.

**Description:** describes the site's intended function.

**Membership Type:** can be open, restricted, or private. An open site appears in the My Sites portlet and users can join and leave the site whenever they want. A restricted site is the same except that users can only request membership. A site administrator must then explicitly grant or deny users' requests to join. A private site does not appear in the My Sites portlet, and users must be added to it manually by a site administrator.

**Active:** determines whether a site is active or inactive. Inactive sites are inaccessible but can be activated whenever a site administrator wishes.

Once you've created a site, it appears in the Sites page of the control panel. Once the site has been created you can specify more details about the site, and these fall under three main categories: Basic Information, Search Engine Optimization, and Advanced.

![Figure 12.5: Editing a Site](../../images/01-site-editor.png)

**Details:** lets you edit the information you entered when you created the site and allows you to choose a site template for the public or private pages of your site. If you select a site template, leave the *Enable propagation of changes from the site template* box checked to automatically update your site if the associated site template changes. The update will only be done to pages which have not been changed within the specific site. If you uncheck this box but recheck it later, the template pages are then reapplied to your site, overwriting any changes that may have been made. Only users who have the permission "Unlink Site Template" will be able to disable the propagation of changes. When the propagation is enabled, the site template might prevent modification of all or certain pages to ensure that the propagation occurs.

**Categorization:** allows you to apply categories and tags to the site.

**Site URL:** lets you set friendly URLs and virtual hosts for your web site.

**Site Template:** provides additional information about the site template associated to the pages of the site (if any).

**Sitemap:** lets you use the sitemap protocol to notify search engines that your web site is available for crawling. 

**Robots:** lets you use a `robots.txt` file to specify certain pages and links that you don't want to be indexed by search engines. You need to set a virtual host before you set a `robots.txt` file.

**Staging:** lets you turn on either Local Live staging or Remote Live staging. To enable staging, the *Enable propagation of changes from the site template* box on the Details tab must be unchecked. With staging enabled, changes to the site template are automatically propagated to the staged site, not to the live site. The changes still must be approved before the site is published to live.

**Analytics:** lets you set a Google Analytics ID that is used for your site. 

When creating a site from a site template, the initial form provides a new option that lets you decide if you want to copy the pages from the template as public pages or as private pages. By default, the site is linked to the site template, and changes to the site template propagate to any site based on it. A checkbox appears that allows users to unlink the site template if the user has permission to do so.

<!-- | TODO: Add screenshot of form used to create a site from a site template | -->

Site templates are very powerful for managing many similiar sites. Let's look further at how they work. 

#### Site Templates [](id=lp-6-1-ugen12-site-templates-0)

Site Templates can be administered in the control panel, within the portal section of the left menu.

Creating or modifying a site template is done using the same tools used to manage a site. You can use these tools to add a hierarchy of pages. Each page can have any configuration and any number of applications, just like a regular site. When you create a site using a site template, the configuration of pages and applications are copied from the template to the site. By default, all changes made to the site template are automatically copied to sites based on that template.

Site templates can also contain content just like actual sites. This allows you to use a site template to create sample content that appears in your site when it is first created. Changes to a site template's content, however, are not propagated to existing sites that are linked to the site template.

---

![tip](../../images/01-tip.png) **Tip:** If you want to publish a piece of web content to many sites and ensure that modifications are applied to all, don't use site template content for that purpose. Instead, place the content in the global scope and then reference it from a *Web Content Display* application in each site.

---

By default, the following site templates are provided:

- **Community Site:** Provides a preconfigured site for building online communities. The home of a *community site* provides message boards, search, a display of a poll and user statistics of the activity of the members of the community. The site will also be created with a page for a community calendar and a page for a wiki.

- **Intranet Site:** Provides a sample preconfigured site for an intranet. The Home page displays the activities of the members of the site, search, a language chooser and a list of the recent content created in the intranet. It also provides 3 additional pages for *Documents and Media*, *Calendar* and external *News* obtained through public feeds.

The following figure displays the form shown when editing the *Community Site* template:

![Figure 12.6: Site Templates](../../images/01-site-templates.png)

To view and manage the pages of a site template, click the *Open site template* link. This opens the template in a new browser window (or tab) and it can be navigated or managed like you would do for a regular site..

<!-- | TODO: I would change the example below to not use organizations to simplify things | -->

For example, let's suppose that we need to create sites for three suborganizations of the Nosester organization: Engineering, Marketing, and Legal. These are to be private sites designed for each organization's internal use. We could design each site separately but we can save ourselves some work if we create a site template to use instead.

To create a site template, navigate to the control panel and click *Site Templates*. Then click *Add* and enter a name for your template: we'll use *Organization Site Template* for our example. Leave the *Active* and *Allow Site Administrators to Modify the Pages Associated with This Site Template* boxes checked. The *Active* box needs to be checked in order for your template to be usable. If your template is still a work in progress, you can uncheck it so that no one uses it until it's ready. Checking *Allow Site Administrators to Modify the Pages Associated with This Site Template* allows Site Administrators to modify or remove the pages and portlets that the template introduces to their sites--if you want the templates to be completely static, you should uncheck this.

Click on the *Open site template* link to begin adding pages and portlets and configuring the layouts. For our example, we would like our template to include four pages: a Home page with the Activities,  Announcements, and Calendar portlets, a Documents and Media page with the Documents and Media portlet, a Wiki page with the Wiki portlet and a Tag Cloud portlet, and a Message Boards page with the Message Boards and Tag Cloud portlets. The changes are automatically saved as you make them, so once you're finished, return to the Site Templates page of the control panel and select *Save*.

![Figure 12.7: You can see the name of the site template you're currently editing](../../images/editing-site-template.png)

Now let's create the Engineering, Marketing, and Legal organizations whose sites we want to create with our template. Go to the control panel and click *Users and Organizations*. Then click the *Add* button and select *Regular Organization*. Enter a name for your organization, select the *Organization site* tab, and check the *Create Site* box. When you check this box, two drop-down lists appear: one for the site's Public Pages and one for its Private Pages. To use your template to create the site, select the name of your template, *Organization Site*, from the Private Pages drop-down list. Click *Save* to create your site.  You can view the new site by clicking the *Open private pages* link from the newly created organization page. The new site will have all the pages and portlets you created in the template. This feature streamlines the site creation process for administrators, making it easy to quickly create sites. Next, let's discuss how to create and apply page templates.

### Page Templates [](id=lp-6-1-ugen12-page-templates-0)

Page templates function similarly to site templates but at the page level. Page templates provide a pre-configured page to reuse. Within a page template it is possible to set up a theme, a layout and specific applications and their configuration. Both sites and site templates can utilize page templates for creating new pages.

![Figure 12.8: Page Templates](../../images/server-configuration-page-templates.png)

The Page Templates page of the control panel shows a list of created page templates and lets you create new ones. It also allows you to edit existing templates and configure their permissions. By default three sample page templates are provided:

- Blog: provides a page with three applications related to blogging. It has two columns, the main left column contains the blogs portlet and the small right column provides two side portlets, tags cloud and recent bloggers. The tag cloud application will show the tags used within the site and will allow navigating through the blog entries shown in the main blogs portlet.
- Wiki: provides a page with three applications related to authoring a wiki. It also has two columns, the main left column with the wiki application and two right side portlets to allow navigating through pages by tags and categories.
- Content Display Page: provides a page that is preconfigured to display content. It has three auxiliary applications (tags navigation, categories navigation and search) and an Asset Publisher. The most significant aspect of this page is that the Asset Publisher is preconfigured to be display any web content that is associated with this page. Because of that when creating a web content it will be possible to select any page created from this page template and a unique (canonical) URL for the web content pointing to this page will be created for it.

To add a new page template, click the *Add* button. Then enter a name and description for your template. Leave the *Active* button checked. Click *Save* and then identify your page template in the list. Click its name or use the Actions button to edit the page template. The *Open Page Template* link opens a new browser window which you can use to configure your new page. Any changes you make are automatically saved so you can close the new browser window once you're done.

Note that after a new page template has been created the default permissions are to only allow the creator to use the page template. In order to provide access to it to other users, use the actions menu in the list of templates and choose *Permissions*. Once you see the matrix of roles and permissions, check the *View* permission for the role or roles that are needed to see the page template in the list of available page templates when creating a new page. If you want any user who can create a page to be able to use the page template, just check the *View* permission for the *User* role.

![Figure 12.9: Selecting a Page Template](../../images/control-panel-selecting-page-template.png)

To use your template to create a new page, just navigate to a page over which you have site administrator privileges and select *Add* &rarr; *Page* from the Dockbar. You'll be able to select a page template and type a name for the new page. Alternatively, you can use the control panel. First, in the context selector menu, select the site to which you'd like to add a page and then click on the *Site Pages* link. Then click the *Add Page* button, type a name, select your template from the drop down menu, and click *Add Page* to finish.

![Figure 12.10: Choosing whether or not to automatically apply page template changes to live pages](../../images/automatic-application-page-template-changes.png)

Note that by default, when a site administrator creates a page based on a page template, any future changes to the template are automatically propagated to your page. Site administrators can disable this behavior by editing the page unchecking the *Automatically apply changes done to the page template* box.

<!-- | COMMENT FOR AUTHOR: IMHO, the following paragraph does not fit here because it is of interest in the context of managing a site, not in the context of managing a site template | -->

If staging has been enabled, changes to the page template are automatically propagated to the staged page. These changes still need to be approved before the page is published to live. For this reason, the automatic propagation of page template changes to the staged page cannot be turned off and the *Automatically apply changes done to the page template* checkbox does not appear.

Now that we've looked at site and page templates, let's discuss how to set up and manage user groups.

![EE Only Feature]
### Exporting and Importing Site Templates and Page Templates

If you want to export a site that uses site or page Templates to a different environment (trough a LAR file or remote publication), the Templates must be exported and imported manually in advance, or the import will fail.

To export a Site using a Site Template, use the following process:
1. Go to Control Panel &rarr; Site Templates and click Actions &rarr; Manage Pages for the Site Template that your site is using. 
2. Click *Export* to obtain a LAR file with the content of the Site Template. Be sure to choose the applications and data you want exported. 
3. In your target environment, go to Control Panel &rarr; Site Templates, and create a new Site Template.
4. Click Actions &rarr; Manage Pages for that Site Template and then click *Import*.
5. Upload the LAR file containing your site template's content. 

Now the site can be exported and imported normally to this new environment.

For page templates, the process very similar: 
1. Go to Control Panel &rarr; Page Templates. 
2. Next to the page template you would like to export, click Actions &rarr; Export. This produces a LAR file that can you later import. 
3. On the target environment, go to Control Panel &rarr; Page Templates, and create a new Page Template
4. Next to the new template, click Actions &rarr; Import. 
5. Upload the LAR file containing the exported page template from step 3

The page template can now be imported normally to this new environment.

### User Groups [](id=lp-6-1-ugen12-user-groups-0)

User Groups are arbitrary groupings of users. These groups are created by portal administrators to group users together who don't necessarily share an obvious hierarchical attribute. Users can be assigned to multiple user groups. User Groups are most often used to achieve one of the following goals:

- Simplify the assignment of several roles to a group of users. For example, in a University portal, a user group could be created to group all teachers independently of their organization to make it easier to assign one or several roles at once to all the teachers.
- Simplify membership to one or more sites by specifying a group of users. Using the previous example, all teachers could be members of the sites *University Employees* and *Students and Teachers Collaboration Site* by adding the *Teachers* user group as a member.
- Provide predefined public or private pages to the users that belong to the user group. For example, the *Teachers* user group could be created to ensure that the home page on all teachers' personal sites has the same layout and applications.

Creating a user group is easy. Navigate to the control panel, click the *Users Groups* link, and then click the *Add* button. There are only two fields to fill out: Name and Description. Click *Save* and you will be redirected back to the *User Groups* page of the control panel.

![Figure 12.11: Creating a New User Group](../../images/server-configuration-new-user-group.png)

Note in the figure above how each user group may have a site, with public and private pages. This is a special type of site that determines the base pages on all user group members' personal sites. The user group site works in a similar way to Site Templates, except that in this case the the User Group Site pages are not copied for each user, but are rather shown dynamically along with any custom pages that the user may have on his/her personal site. For this reason, users are not allowed to make any modifications to the pages that are *inherited* from the user group. Alternatively the administrators of the user group can define certain areas as customizable, just like they can for regular sites. This allows users to decide which applications they want to place in certain areas of each page, as well as change their configuration.

![Figure 12.12: User Group Actions](../../images/01-editing-a-user-group.png)

As with the other resources in the portal, you can click the *Actions* button next to a user group to perform various operations on that group.

**Edit:** allows you to modify the name or description of the user group.

**Permissions:** lets you define which roles have permissions to view, edit, delete, assign members to the user group, etc.

**Site Permissions:** lets you define which roles have permissions to manage the user group site, to specify who can administer its pages, export and import pages and portlet content, manage archived setups, and configure its applications. 

**Manage Site Pages:** allows you to add pages to the user group site, import or export pages, organize the page hierarchy, modify the look and feel of the pages, add a logo, or access other options from the Manage Site interface.

**Assign Members:** lets you search for and select users in the portal to be assigned to this user group as well as view the users currently belonging to the user group .

**Delete:** deletes the user group.

If your user group has a site, two options named **Go to the Site's Public Pages** and **Go to the Site's Private Pages** also appear as links in your user group's Actions menu. Clicking one of these links opens the user group's site in a new browser window. Any changes you make to the site are saved automatically. You can safely close the browser window when you're done.

##### Creating and editing a User Group [](id=lp-6-1-ugen12-creating-and-editing-a-user-group-0)

A user group's site can be administered from the control panel. Select *User Groups* from the control panel to see a list of existing user groups. To edit a user group, click on its name or description. You can also click on the *Actions* button to see the full list of actions that can be performed on a user group. When editing a user group, you can view its site, if it exists, by clicking the *Open Pages* link under Public Pages or Private Pages (read below for details on user group sites).

As an example of how user group sites can be used, let's create a user group called *Bloggers* along with a simple template. We'll call the site template *Bloggers* too. It should contain a single *Blog* page with the Blogs and Recents Bloggers portlets on it. First, navigate to the User Groups page of the control panel. Then click *Add* and enter the name *Bloggers* for your user group, and optionally, a description. Click *Save* to create your user group.

Our next step is to assign an existing user to the *Bloggers* group.

##### Assigning Members to a User Group [](id=lp-6-1-ugen12-assigning-members-to-a-user-group-0)

Navigate to *Users and Organizations* and create a new user called *Joe Bloggs*. Then navigate to the User Groups page of the control panel and click *Actions* &rarr; *Assign Members* next to the Bloggers group. Click the *Available* tab to see a list of users that can be assigned to the group.

![Figure 12.13: Assigning Members to a User Group](../../images/01-adding-members-to-user-group.png)

From that list, one or more users can be selected to be assigned as members of the user group.

For example, by default, newly created users are given *Welcome* pages on the public pages portion of their personal sites. This Welcome page contains the Language, Search, and Blogs portlets. You can see the effect of the *Bloggers* site template on the public pages of Joe Bloggs's personal site in the figure above. When Joe Bloggs was added to the *Bloggers* group, he received a *Blogs* page with the *Blogs* and *Recent Bloggers* portlets.

After the user group has been created and several users have been added to it, you can add all those users at once as members of a site in one step from the *Site Memberships* UI of the site. You can also use the user group when assigning a role to users from the roles management UI.

The next section describes a more advanced usage of user groups: User Group Sites.

#### User Group Sites [](id=lp-6-1-ugen12-user-group-sites-0)

Liferay allows users to each have a personal site consisting of public and private pages. Permissions can be granted to allow users to customize their personal sites at will. Originally, the default configuration of those pages could only be determined by the portal administrator through the `portal-ext.properties` file and, optionally, by providing the configuration in a LAR file. You can still configure it like this, but it isn't very flexible or easy to use.

By using User Group Sites, portal administrators can add pages to the personal sites of all the users who belong to the site in an easy and centralized way. All the user group site's public pages are shown as part of the user's public personal site. All the user group site's private pages are shown as part of the user's private site. If a user belongs to several user groups, all of its pages are made part of his public and private site. In an educational institution's portal, for example, teachers, staff, and students could get different default pages and applications on their personal sites.

The pages that a user personal site *inherits* from a User Group still belong to the User Group and thus cannot be changed in any way by the users. What the user group administrators can do is define certain areas of the pages as customizable to allow the users to choose which applications and what configuration should be shown in those areas. If a user has permission to add custom pages to his/her personal site, besides those *inherited* from a user group, the custom pages are always shown last.

Since the *inheritance* of pages is done dynamically, this new system introduced in Liferay 6.1 can scale to hundreds of thousands of users or even millions of them without an exponential impact in performance. Previous versions of Liferay used a different technique that required that the user group pages were copied to each user's personal site. For portals upgrading from previous versions of Liferay, you can keep the old behavior, but it has been left disabled by default. You can enable it by adding the following line to your portal-ext.properties file:

	user.groups.copy.layouts.to.user.personal.site=true

When this property is set to true, once the template pages have been copied to a user's personal site, the copies may be modified by the user. Changes done to the originals in the User Group will only affect new users added to the user group. Users with administrative privileges over their personal sites can modify the pages and their content provided that the *Allow Site Administrators to Modify the Pages Associated with This Site Template* box has been checked for the template. When a user is removed from a user group, the associated pages are removed from the user's personal site. Moreover, if a user is removed from a group and is subsequently added back, the group's template pages are copied to the user's site a second time. Note that if a user group's site is based on a site template and an administrator modifies the user group's site template after users have already been added to the group, those changes only take effect if the *Enable propagation of changes from the site template* box for the user group was checked.

---

![tip](../../images/01-tip.png) **Tip:** Previous to Liferay 6.1, pages from different user groups could be combined on users' personal sites by using a naming convention. Liferay 6.1 simplifies the way user groups' sites work by disallowing page combination. Set the property *user.groups.copy.layouts.to.user.personal.site* to true if you depend on that functionality.

---

You can create a user group's site manually or base it on a site template. To create a user group's site manually, use the *Actions* menu mentioned above and choose *Manage Site Pages*. You can add a new public or private page by selecting the appropriate tab and then clicking the *Add Page* button. Once the user group has at least one public or private page in place, you can go back to the *Actions* menu and click on the *Go to the Site's Public Pages* or *Go to the Site's Private Pages* link to open the user group's site in a new browser window. In the new window, you can add more pages and portlets and configure site settings.

You can also base a user group's site on a template. When editing a user group, use the Public Pages and Private Pages drop down lists to select a site template. Leave the *Enable propagation of changes from the site template* box checked to automatically update users' personal sites if the associated site template changes. If you uncheck this box but recheck it later, the template pages are copied to the users' sites, overwriting any changes they may have made. You can allow users to make changes to the pages they receive from the user group by enabling the customization options on each page.

This flexibility lets you achieve almost any desired configuration for a user's personal site without having to modify it directly. When a user is assigned to a user group, the configured site pages are copied directly to the user's personal site.

Following with the example above, we will create a site for our sample user group. Edit the *Bloggers* group. Choose an existing Site Template from the drop down menu for the user group's public pages and click *Save*. After the page reloads you can click to see the pages and make any changes desired, add additional pages, etc.

![Figure 12.14: Selecting a Template for the User Group Site](../../images/user-group-site-template-selected.png)

Also, try visiting the public site of one of the users that belong to the user group. You will see how all of the pages in the user group appear as part of the user site, including the ones copied from the site template and the ones added afterwards.

### Roles [](id=lp-6-1-ugen12-roles-0)

Roles are groupings of users that share a particular function within the portal, according to a particular scope. Roles can be granted permissions to various functions within portlet applications. You can think of a role as a description of a function, such as Message Board Administrators. A role with that name is likely to have permissions relevant to the specific Message Board portlets delegated to it. Users who are placed in this role will inherit these permissions.

The roles page of the control panel serves as a single interface which lets you create roles, assign permissions to them, and assign users to the roles. Roles can be scoped by portal, site, or organization. To create a role, click the *Roles* link, and then click the *Add* button. You can choose a Regular, Site, or Organization role. A regular role is a portal-scoped role. Make a selection and then type a name for your role, a title, and a description. The name field is required but the title and description are optional. If you enter a name and a title, the title will be displayed in the list of roles on the Roles page of the control panel. If you do not enter a title, the name will be displayed. When you have finished, click *Save*.

![Figure 12.15: Roles Page and Role Actions Menu](../../images/01-roles-and-role-actions.png)

After you save, Liferay redirects you to the list of roles. To see what functions you can perform on your new role, click the *Actions* button.

**Edit:** lets you change the name, title, or description of the role.

**Permissions:** allows you to define which users, user groups, or roles have permissions to edit the role.

**Define Permissions:** defines what permissions this role grants. This is outlined in the next section.

**Assign Members:** lets you search and select users in the portal to be assigned to this role. These users will inherit any permissions that have been assigned to this role.

**View Users:** allows you to view the users who have been assigned to this role.

**Delete:** permanently removes a role from the portal.

Next, let's examine how to configure the permissions granted by different roles.

#### Defining Permissions on a Role [](id=lp-6-1-ugen12-defining-permissions-on-a-role-0)

Roles serve as repositories of permissions to be assigned to users who belong to them. So, to use a role, you need to assign members to it and define the permissions that you want to grant to members of the role.

![Figure 12.16: Defining Permissions on a Role](../../images/01-defining-permissions-on-a-role.png)

When you click the *Actions* button on portal-scoped role and select *Define Permissions*, you will be shown a list of all the permissions that have been defined for that role. Click the *Add Permissions* drop-down menu to see a list of the permissions that can be defined. As of Liferay version 6.1, these permissions fall into seven categories: Portal, Site Content, Site Application, Control Panel: Personal, Control Panel: Site, Control Panel: Portal, and Control Panel: Server. For non-portal scoped roles, you need to click on the *Options* link on individual portlets, then *Configuration*, then *Permissions* to assign permissions within the site or organization that owns the portlet. 

Portal permissions cover portal-wide activities that comprise several categories, such as site, organization, location, password policy, etc. This allows you to create a role that, for example, can create new sites within the portal. This would allow you to grant users that particular permission without making them overall portal administrators.

Site Content permissions cover the content that the installed portlets create. If you pick one of the portlets from this list, you'll get options for defining permissions on its content. For example, if you pick Message Boards, you'll see permissions for creating categories or threads, or deleting and moving topics.

Site Application permissions affect the application as a whole. So, using our Message Boards example, an application permission might define who can add the Message Boards portlet to a page.

The control panel permissions affect how the portlet appears to the user in the control panel. Some control panel portlets have a Configuration button, so you can define who gets to see that, as well as who gets to see an application in the control panel.

![Figure 12.17: Message Board Content Permissions](../../images/01-message-board-content-permissions.png)

Each possible action to which permissions can be granted is listed. To grant a permission, check the box next to it. If you want to limit the scope of the permission to a particular site, click the *Limit Scope* link, and then choose the site. Once you have chosen the permissions granted to this role, click *Save*. For a portal-scoped Message Boards Administrator role, you might grant content permissions for every action listed. After you click *Save*, you will see a list of all permissions that are currently granted to this role. From here, you can add more permissions or go back by clicking a link in the breadcrumb list or the *Return to Full Page* link.

Roles are very powerful, and allow portal administrators to define various permissions in whatever combinations they like. This gives you as much flexibility as possible to build the site you have designed.

#### Special Note about the Power Users Role [](id=lp-6-1-ugen12-special-note-about-the-power-users-role-0)

Prior to Liferay 6.0, the default configurations of many Liferay portlets allowed power users, but not regular users, to access them. Liferay 6.0 and subsequent versions grant the same default permissions to both power users and regular users. This way, portal administrators are not forced to use the power users role. However, Liferay encourages those who do to create their own custom permissions for the role. 

---

![tip](../../images/01-tip.png) Note: Prior to Liferay version 6.0, Power Users and Users did *not* have the same default permissions. So if are using Liferay 5.2 or a previous version, it's dangerous to remove the Power Users role from the default user associations: this could remove certain permissions that you expect to apply to all users. If you decide to remove the Power Users role from the default user associations anyway, you will probably want to modify the permissions on certain portlets to make them accessible to all users. To do this, see the section on Plugins Configuration below.

---

Liferay 6.0 introduced a new feature to Liferay's permissions system: teams. Let's examine them next.

### Teams [](id=lp-6-1-ugen12-teams-0)

Teams don't appear as a link in the control panel because they exist *within* sites. Teams allow site administrators a greater degree of flexibility than was possible using just user groups and roles. They allow site administrators to create various sets of users and permissions for site-specific functions. Teams are the preferred method for collecting permissions within a single site. 

If you create a team for one site, the permissions defined for it are not available to any other sites. In contrast, if you assigned a custom role to a user group, the role would be available portal-wide even though the specific permissions defined by it would only apply within the scope of a designated site. Furthermore, team members, unlike user group members, are guaranteed to be members of the desired site.

To create a team within a site, first naviagte to the *Control Panel &rarr; Sites* page then and then select *Actions &rarr; Manage Memberships* for the site within which you want to create a team. Finally, click *View &rarr; Teams* and click the Add Team button.

![Figure 12.18: Creating a Team within a Site](../../images/01-creating-a-team.png)

After you've clicked the *Add Team* button and entered a name and a description, click *Save*. Your new team will appear in the list. To add members, simply click on *Actions &rarr; Assign Members*.

Permission management for teams is handled at the individual portlet level, using the *Options &rarr; Configuration &rarr; Permissions* tab of the portlet itself. Remember that the portlet options link is the wrench symbol at the top of a portlet. This enables users who wouldn't have access to all of the necessary options in the control panel to manage permissions through teams.

[Assigning Portlet Permissions to a Team](../../images/01-assigning-portlet-permissions-to-teams)

To give a team access to a particular portlet function, access the *Permissions* tab of a portlet residing on a page, check the boxes corresponding to permissions you want to assign to the teams, and then click *Save*. That's it! Now your team is ready to perform their functions. Next, let's look at how to configure Liferay's portal settings.

## Managing Portal Settings [](id=managing-portal-settings)

After you have created users, user groups, organizations, roles, sites, and teams, your portal will be ready to host content and applications. You can configure Liferay's portal settings to fit your environment and your particular portal project. Many configurations can be performed through Liferay's portlet-driven user interface. This section covers how to configure portal settings such as password policies, authentication settings, mail host names, email notifications, display settings, and monitoring.

Now that you have been navigating in the control panel, you should be pretty familiar with how it works. All the options appear in the left navigation, their interfaces appear in the middle, and any sub-options appear on the right. We have focused so far on the maintenance of users and portal security. The remaining links in the *Portal* category focus on various portal settings which cover how the portal operates and integrates with other systems you may have. Let's begin our discussion of Liferay's portal settings by examining how to configure password policies.

### Password Policies [](id=lp-6-1-ugen12-password-policies-0)

Password policies can enhance the security of your portal. You can set requirements on password strength, frequency of password expiration, and more. Additionally, you can apply different password policies to different sets of portal users.

If you are viewing a page other than the control panel, select *Control Panel* from the *Go to* menu of the Dockbar. Next, click on the *Password Policies* link on the left side of the screen under the *Portal* heading. You will see that there is already a default password policy in the system. You can edit this in the same manner as you edit other resources in the portal: click *Actions* and then click *Edit*.

The Password Policy settings form contains the following fields. Enabling specific settings via the check boxes prompts setting-specfic options to appear.

**Name:** requires you to enter a name for the password policy.

**Description:** lets you describe the password policy so that other administrators will know what it's for.

**Changeable:** determines whether or not a user can change his or her password.

**Change Required:** determines whether or not a user must change his or her password after logging into the portal for the first time.

**Minimum Age:** lets you choose how long a password must remain in effect before it can be changed.

**Reset Ticket Max Age:** determines how long a password reset link remains valid.

**Password Syntax Checking:** allows you to set a minimum password length and to choose whether or not dictionary words can be in passwords. You can also specify detailed requirements such as minimum numbers of alpha numeric characters, lower case letters, upper case letters, numbers, or symbols.

**Password History:** lets you keep a history (with a defined length) of passwords and prevents users from changing their passwords to one that was previously used.

**Password Expiration:** lets you choose how long passwords can remain active before they expire. You can select the age, the warning time, and a grace limit.

**Lockout:** allows you to set a number of failed log-in attempts that triggers a user's account to lock. You can choose whether an administrator needs to unlock the account or if it becomes unlocked after a specific duration.

From the list of password policies, you can perform several other actions.

**Edit:** brings you to the form above and allows you to modify the password policy.

**Permissions:** allows you to define which users, user groups, or roles have permission to edit the password policy.

**Assign Members:** takes you to a screen where you can search and select users in the portal to be assigned to this password policy. The password policy will be enforced for any users who are added here.

**Delete:** shows up for any password policies that you add beyond the default policy. You cannot delete the default policy.

Next, let's examine Liferay's Portal Settings.

<!-- (JR) start here 19jan2012 -->

### Portal Settings [](id=lp-6-1-ugen12-portal-settings-0)

Most global portal settings can be configured from the Portal Settings section of the control panel. The Configuration heading contains the following links:

**General:** lets you configure global settings, such as the company name, domain, the virtual host, a global portal logo, and more.

**Authentication:** allows you to configure log in IDs, connection to LDAP, and Single Sign-On.

**Users:** has three tabs, labeled Fields, Reserved Credentials, and Default User Associations. The Fields tab enables or disables some user fields, such as birthday or terms of use. The Reserved Credentials tab lets you reserve screen names and email addresses so that users cannot register using them. You might use this to prevent users from registering on the portal with user names that contain profanity or that sound official, such as *admin* or *president*. The Default User Associations tab lets you configure default membership to roles, user groups, and sites for new users, and provides a check box which allows you to retroactively apply these to existing users.

**Mail Host Names:** lets you add a list of other mail host names to be associated with your organization. For example, your main domain might be `mycompany.com`, but you might use `mycompany-marketing.com` for your email newsletters. Any domain names associated with your organization can go here.

**Email Notifications:** allows you to configure Liferay to send email notifications for certain events, such as user registrations, password changes, etc. You can customize those messages here.

![Figure 12.19: Portal Settings Pages](../../images/server-configuration-portal-settings-pages.png)

Let's discuss these settings next.

#### General [](id=lp-6-1-ugen12-general-0)

The General link takes you to a page with three headings: Main Configuration, Navigation, and Additional Information. Under the Main Configuration heading, you can set the name of the company, organization, or site which is running the portal. This name also defines the name of your portal's default site. Its default name is `liferay.com`, so you will definitely want to set this to reflect your own company. You can also set the mail domain, virtual host, and content delivery network address here. Under the Navigation heading, you can set a home page for your portal here as well as default landing and logout pages. Under the Additional Information heading, you can specify a Legal name, ID, and type for your company, an SIC code, a ticker symbol, and industry, and a type.

#### Authentication [](id=lp-6-1-ugen12-authentication-0)

The Authentication page has several tabs: General, LDAP, CAS, Facebook, NTLM, OpenID, Open SSO, and SiteMinder. You can use any of these authentication methods to configure how users will authenticate to Liferay. Since Liferay supports quite a few authentication methods, there are different settings for each.

The settings on the General tab of the Authentication page affect only Liferay functionality, and don't have anything to do with the integration options on the other tabs. The General tab allows you to customize Liferay's standard authentication behavior. Specifically, the General tab allows you to select from several global authentication settings:

-   Authenticate via email address (default), screen name, or user ID (a numerical ID auto-generated in the database not recommended).

-   Enable/Disable automatic log in. If enabled, Liferay allows a user to check a box which will cause the site to "remember" the user's log in by placing a cookie on his or her browser. If disabled, users will always have to log in manually.

-   Enable/Disable forgotten password functionality.

-   Enable/Disable request password reset links.

-   Enable/Disable account creation by strangers. If you are running an Internet site, you will probably want to leave this on so that visitors can create accounts on your site.

-   Enable/Disable account creation by those using an email address in the domain of the company running the site (which you just set on the General page of Portal Settings). This is handy if you are using Liferay to host both internal and external web sites. You can make sure that all internal IDs have to be created by administrators, but external users can register for IDs themselves.

-   Enable / Disable email address verification. If you enable this, Liferay will send users a verification email with a link back to the portal to verify that the email address they entered is a valid one they can access.

By default, all settings except for the last are enabled. User authentication by email address is an important default for the following reasons:

1.  An email address is, by definition, unique to the user who owns it.

2.  People can generally remember their email addresses. If you have  user who hasn't logged into the portal for a while, it is possible that he or she will forget his or her screen name, especially if the user was not allowed to use his or her screen name of choice (because somebody else already used it).

3.  If a user changes his or her email address, it is more likely that the user will forget to update his or her email address in his or her profile, if that email address is not used to authenticate. If the user's email address is not updated, all notifications sent by the portal will fail to reach the user. So it is important to keep the email address at the forefront of a user's mind when he or she logs in to help the user keep it up to date. 

We'll examine how to set up LDAP authentication next.

##### Authentication: LDAP [](id=lp-6-1-ugen12-authentication-ldap-0)

You can use the LDAP tab of the Authentication page to connect Liferay to an LDAP directory. There are two places for you to configure the LDAP settings: here in the control panel or in the `portal-ext.properties` file (which is covered in chapter 14). We recommend that you use the control panel since your configuration settings will be stored in the database. Note that if you use both, the settings in the database will override the settings in `portal-ext.properties`. Configuring the LDAP settings from the control panel is easier and does not require a restart of Liferay. The only compelling reason to use the `portal-ext.properties` file is if you have many Liferay nodes which will be configured to run against the same LDAP directory. In that case, for your initial deployment, it may be easier to copy the `portal-ext.properties` file to all of the nodes so that the first time they start up, the settings are correct. Regardless of which method you use, the available settings are the same.

You configure the global values from the LDAP tab of the Authentication page.

**Enabled:** Check this box to enable LDAP Authentication.

**Required:** Check this box if LDAP authentication is required. Liferay will then not allow a user to log in unless he or she can successfully bind to the LDAP directory first. Uncheck this box if you want to allow users with Liferay accounts but no LDA accounts to log in to the portal.

**LDAP Servers:** Liferay supports connections to multiple LDAP servers. You can you the Add button beneath this heading to add LDAP servers. We explain how to configure new LDAP servers below.

**Import/Export:** You can import and export user data from LDAP directories using the following options:

* *Import Enabled:* Check this box to cause Liferay to do a mass import from your LDAP directories. If you want Liferay to only synchronize users when they log in, leave this box unchecked. Definitely leave this unchecked if you are working in a clustered environment. Otherwise, all of your nodes would try to do a mass import when each of them starts up.

* *Import on Startup Enabled:* Check this box to have Liferay run the import when it starts up. Note: This box only appears if you check the *Import Enabled* box above.

* *Export Enabled:* Check this box to enable Liferay to export user accounts from the database to LDAP. Liferay uses a listener to track any changes made to the `User` object and will push these changes out to the LDAP server whenever the `User` object is updated. Note that by default on every login, fields such as `LastLoginDate` are updated. When export is enabled, this has the effect of causing a user export every time the user logs in. You can disable this by setting the following property in your `portal-ext.properties` file:

    users.update.last.login=false

**Use LDAP Password Policy:** Liferay uses its own password policy by default. This can be configured on the Password Policies page of the control panel. Check the *Use LDAP Password Policy* box if you want to use the password policies defined by your LDAP directory. Once this is enabled, the Password Policies tab will display a message stating that you are not using a local password policy. You will now have to use your LDAP directory's mechanism for setting password policies. Liferay does this by parsing the messages in the LDAP controls that are returned by your LDAP server. By default, the messages in the LDAP controls that Liferay is looking for are the messages that are returned by the Fedora Directory Server. If you are using a different LDAP server, you will need to customize the messages in Liferay's `portal-ext.properties` file, as there is not yet a GUI for setting this. See below for instructions describing how to do this.

Once you've finished configuring LDAP, click the *Save* button. Next, let's look at how to add LDAP servers.

###### Adding LDAP Servers [](id=lp-6-1-ugen12-adding-ldap-servers-0)

The Add button beneath the LDAP servers heading allows you to add LDAP servers. If you have more than one, you can arrange the servers by order of preference using the up/down arrows. When you add an LDAP Server, you will need to provide several pieces of data so that Liferay can bind to that LDAP server and search it for user records. Regardless of how many LDAP servers you add, each server has the same configuration options.

**Server Name:** Enter a name for your LDAP server.

**Default Values:** Several leading directory servers are listed here. If you are using one of these, select it and click the Reset Values button. The rest of the form will be populated with the proper default values for that directory.

**Connection:** These settings cover the basic connection to LDAP.

* *Base Provider URL:* This tells the portal where the LDAP server is located. Make sure that the machine on which Liferay is installed can communicate with the LDAP server. If there is a firewall between the two systems, check to make sure that the appropriate ports are opened.

* *Base DN:* This is the Base Distinguished Name for your LDAP directory. It is usually modeled after your organization. For a commercial organization, it may look similar to this: `dc=companynamehere,dc=com`.

* *Principal:* By default, the administrator ID is populated here. If you have removed the default LDAP administrator, you will need to use the fully qualified name of the administrative credential that you use instead. You need an administrative credential because Liferay will be using this ID to synchronize user accounts to and from LDAP .

* *Credentials:* This is the password for the administrative user.

This is all you need in order to make a regular connection to an LDAP directory. The rest of the configuration is optional. Generally, the default attribute mappings provide enough data to synchronize back to the Liferay database when a user attempts to log in. To test the connection to your LDAP server, click the *Test LDAP Connection* button.

If you are running your LDAP directory in SSL mode to prevent credential information from passing through the network unencrypted, you will have to perform extra steps to share the encryption key and certificate between the two systems.

For example, assuming your LDAP directory happens to be Microsoft Active Directory on Windows Server 2003, you would take the following steps to share the certificate:

On the Windows 2003 Domain Controller, open the *Certificates* MMC snapin. Export the Root Certificate Authority certificate by selecting *Certificates (Local Computer) mmc snapin &rarr; Trusted Root Certification Authorities &rarr; MyRootCACertificateName*. Right click this certificate and select *All Tasks &rarr; export &rarr; select DER encoded binary X.509 .CER*. Copy the exported `.cer` file to your Liferay Portal server.

As with the CAS install (see the below section entitled Single Sign-On), you will need to import the certificate into the *cacerts keystore*. The import is handled by a command like the following:

    keytool -import -trustcacerts -keystore
    /some/path/jdk1.5.0_11/jre/lib/security/cacerts -storepass changeit
    -noprompt
    -alias MyRootCA -file /some/path/MyRootCA.cer

The *keytool* utility ships as part of the Java SDK.

Once this is done, go back to the LDAP page in the control panel. Modify the LDAP URL in the Base DN field to the secure version by changing the protocol to `https` and the port to `636` like the following:

    ldaps://myLdapServerHostname:636

Save the changes. Your Liferay Portal will now use LDAP in secure mode for authentication.

**Users:** This section contains settings for finding users in your LDAP directory.

* *Authentication Search Filter:* The search filter box can be used to determine the search criteria for user logins. By default, Liferay uses users' email addresses for their login names. If you have changed this setting, you will need to modify the search filter here, which has been configured to use the email address attribute from LDAP as a search criterion. For example, if you changed Liferay's authentication method to use screen names instead of the email addresses, you would modify the search filter so that it can match the entered log in name:

    (cn=@screen_name@)

* *Import Search Filter:* Depending on the **LDAP** server, there are different ways to identify the user. Generally, the default setting (`objectClass=inetOrgPerson`) is fine, but if you want to search for only a subset of users or users that have different object classes, you can change this.

* *User Mapping:* The next series of fields allows you to define mappings from LDAP attributes to Liferay fields. Though your LDAP user attributes may be different from LDAP server to LDAP server, there are five fields that Liferay requires to be mapped in order for the user to be recognized. You must define a mapping to the corresponding attributes in LDAP for the following Liferay fields:

    +   *Screen Name*

    +   *Password*

    +   *Email Address*

    +   *Full Name*

    +   *First Name*

    +   *Middle Name*

    +   *Last Name*

    +   *Job Title*

    +   *Group*

The control panel provides default mappings for commonly used LDAP attributes. You can also add your own mappings if you wish.

* *Test LDAP Users:* Once you have your attribute mappings set up (see above), click the *Test LDAP Users* button, and Liferay will attempt to pull LDAP users and match them with their mappings as a preview.

![Figure 12.20: Testing LDAP Users](../../images/server-configuration-testing-ldap-users.jpg)

**Groups:** This section contains settings for mapping LDAP groups to Liferay.

* *Import Search Filter:* This is the filter for finding LDAP groups that you want to map to Liferay. Enter the LDAP group attributes that you want retrieved for this mapping. The following attributes can be mapped:

    + Group Name

    + Description

    + User

* *Test LDAP Groups:* Click the **Test LDAP Groups** to display a list of the groups returned by your search filter.

**Export:** This section contains settings for exporting user data from LDAP.

* *Users DN:* Enter the location in your LDAP tree where the users will be stored. When Liferay does an export, it will export the users to this location.

* *User Default Object Classes:* When a user is exported, the user is created with the listed default object classes. To find out what your default object classes are, use an LDAP browser tool such as JXplorer to locate a user and view the Object Class attributes that are stored in LDAP for that user.

* *Groups DN:* Enter the location in your LDAP tree where the groups will be stored. When Liferay does an export, it will export the groups to this location.

* *Group Default Object Classes:* When a group is exported, the group is created with the listed default object classes. To find out what your default object classes are, use an LDAP browser tool such as *Jxplorer* to locate a group and view the Object Class attributes that are stored in LDAP for that group.

![Figure 12.21: Mapping LDAP Groups](../../images/server-configuration-mapping-ldap-groups.jpg)

Once you've set all your options and tested your connection, click *Save*. From here, you can add another LDAP server or set just a few more options that apply to all of your LDAP server connections.

###### LDAP Options Not Available in the GUI [](id=lp-6-1-ugen12-ldap-options-not-available-in-the-gui-0)

Although most of the LDAP configuration can be done from the control panel, there are several configuration parameters that are only available by editing `portal-ext.properties`. These options will be available in the GUI in future versions of Liferay Portal, but for now they can only be configured by editing the properties file.

If you need to change any of these options, copy the LDAP section from the `portal.properties` file into your `portal-ext.properties` file. Note that since you have already configured LDAP from the GUI, any settings from the properties file that match settings already configured in the GUI will be ignored. The GUI, which stores the settings in the database, always takes precedence over the properties file.

    ldap.auth.method=bind
    #ldap.auth.method=password-compare

Set either bind or password-compare for the LDAP authentication method. Bind is preferred by most vendors so that you don't have to worry about encryption strategies. Password compare does exactly what it sounds like: it reads the user's password out of LDAP, decrypts it, and compares it with the user's password in Liferay, syncing the two.

    ldap.auth.password.encryption.algorithm=
    ldap.auth.password.encryption.algorithm.types=MD5,SHA

Set the password encryption to used to compare passwords if the property `ldap.auth.method` is set to `password-compare`.

    ldap.import.method=[user,group]

If you set this to `user`, Liferay will import all users from the specified portion of the LDAP tree. If you set this to `group`, Liferay will search all the groups and import the users in each group. If you have users who do not belong to any groups, they will not be imported.

    ldap.error.password.age=age
    ldap.error.password.expired=expired
    ldap.error.password.history=history
    ldap.error.password.not.changeable=not allowed to change
    ldap.error.password.syntax=syntax
    ldap.error.password.trivial=trivial
    ldap.error.user.lockout=retry limit

These properties are a list of phrases from error messages which can possibly be returned by the LDAP server. When a user binds to LDAP, the server can return *controls* with its response of success or failure. These controls contain a message describing the error or the information that is coming back with the response. Though the controls are the same across LDAP servers, the messages can be different. The properties described here contain snippets of words from those messages, and will work with Red Hat's Fedora Directory Server. If you are not using that server, the word snippets may not work with your LDAP server. If they don't, you can replace the values of these properties with phrases from your server's error messages. This will enable Liferay to recognize them. Next, let's look at the Single Sign-On solutions that Liferay supports.

#### Single Sign-On [](id=lp-6-1-ugen12-single-sign-on-0)

Single Sign-On solutions allow you to provide a single login credential for multiple systems. This allows you to have people authenticate to the Single Sign-On product and they will be automatically logged in to Liferay and to other products as well.

Liferay supports several single sign-on solutions. Of course, if your product is not yet supported, you may choose to implement support for it yourself by use of the extension environment. Alternatively, your organization can choose to sponsor support for it. Please contact `sales@liferay.com` for more information about this.

##### Authentication: Central Authentication Service (CAS) [](id=lp-6-1-ugen12-authentication-central-authentication-service-cas-0)

CAS is an authentication system that was originally created at Yale University. It is a widely-used open source single sign-on solution, and was the first SSO product to be supported by Liferay.

Please follow the documentation for CAS to install it on your application server of choice.

Your first step will be to copy the CAS client .jar file to Liferay's library folder. On Tomcat, this is in `[Tomcat Home]/webapps/ROOT/WEB-INF/lib`. Once you've done this, the CAS client will be available to Liferay the next time you start it.

The CAS Server application requires a properly configured Secure Socket Layer certificate on your server in order to work. If you wish to generate one yourself, you will need to use the `keytool` utility that comes with the JDK. Your first step is to generate the key. Next, you export the key into a file. Finally, you import the key into your local Java key store. For public, Internet-based production environments, you will need to either purchase a signed key from a recognized certificate authority (such as Thawte or Verisign) or have your key signed by a recognized certificate authority. For Intranets, you should have your IT department pre-configure users' browsers to accept the certificate so that they don't get warning messages about the certificate.

To generate a key, use the following command:

    keytool -genkey -alias tomcat -keypass changeit -keyalg RSA

Instead of the password in the example (`changeit`), use a password that you will be able to remember. If you are not using Tomcat, you may want to use a different alias as well. For First and Last names, enter `localhost`, or the host name of your server. It cannot be an IP address.

To export the key to a file, use the following command:
    
    keytool -export -alias tomcat -keypass changeit -file server.cert

Finally, to import the key into your Java key store, use the following command:

    keytool -import -alias tomcat -file %FILE_NAME% -keypass changeit
    -keystore $JAVA_HOME/jre/lib/security/cacerts

If you are on a Windows system, replace `$JAVA_HOME` above with `%JAVA_HOME%`. Of course, all of this needs to be done on the system on which CAS will be running.

Once your CAS server is up and running, you can configure Liferay to use it. This is a simple matter of navigating to the *Settings &rarr;  Authentication &rarr; CAS* tab in the control panel. Enable CAS authentication, and then modify the URL properties to point to your CAS server.

**Enabled:** Check this box to enable CAS single sign-on.

**Import from LDAP:** A user may be authenticated from CAS and not yet exist in the portal. Select this to automatically import users from LDAP if they do not exist in the portal.

The rest of the settings are various URLs, with defaults included. Change *localhost* in the default values to point to your CAS server. When you are finished, click *Save*. After this, when users click the *Sign In* link, they will be directed to the CAS server to sign in to Liferay.

##### Authentication: Facebook [](id=lp-6-1-ugen12-authentication-facebook-0)

Liferay Portal also enables users to log in using their Facebook accounts. To enable this feature, you simply need to select the *Enable* box and enter the Application ID and Application Secret which should have been provided to you by Facebook. Facebook SSO works by taking the primary Facebook email address and searching for the same email address in Liferay's `User_` table. If a match is found, the user is automatically signed on (provided that user clicked *allow* from the Facebook dialog). If there isn't a match, the user is prompted in Liferay to add a user from Facebook. Once selected, a new user is created by retrieving four fields from Facebook (first name, last name, email address, and gender).

##### Authentication: NTLM [](id=lp-6-1-ugen12-authentication-ntlm-0)

NTLM is a Microsoft protocol that can be used for authentication through Microsoft Internet Explorer. Though Microsoft has adopted Kerberos in modern versions of Windows server, NTLM is still used when authenticating to a workgroup. Liferay Portal now supports NTLM v2 authentication. NTLM v2 is more secure and has a stronger authentication process than NTLMv1.

**Enabled:** Check this box to enable NTLM authentication.

**Domain Controller:** Enter the IP address of your domain controller. This is the server that contains the user accounts you want to use with Liferay.

**Domain:** Enter the domain / workgroup name.

**Service Account:** You need to create a service account for NTLM. This account will be a computer account, not a user account.

**Service Password:** Enter the password for the service account.

##### Authentication: OpenID [](id=lp-6-1-ugen12-authentication-openid-0)

OpenID is a new single sign-on standard which is implemented by multiple vendors. The idea is that multiple vendors can implement the standard, and then users can register for an ID with the vendor they trust. The credential issued by that vendor can be used by all the web sites that support OpenID. Some high profile OpenID vendors are AOL [http://openid.aol.com/screenname](http://openid.aol.com/screenname), LiveDoor [http://profile.livedoor.com/username](http://profile.livedoor.com/username), and LiveJournal [http://username.livejournal.com](http://username.livejournal.com/). Please see the OpenID site [http://www.openid.net](http://www.openid.net/) for a more complete list.

A main benefit of OpenID for the user is that he or she no longer has to register for a new account on every site in which he or she wants to participate. Users can register on *one* site (the OpenID provider's site) and then use those credentials to authenticate to many web sites which support OpenID. Many web site owners often struggle to build communities because end users are reluctant to register for so many different accounts. Supporting OpenID makes it easier for site owners to build their communities because the barriers to participating (i.e., the effort it takes to register for and keep track of many accounts) are removed. All of the account information is kept with the OpenID provider, making it much easier to manage this information and keep it up to date.

Liferay Portal can act as an OpenID consumer, allowing users to automatically register and sign in with their OpenID accounts. Internally, the product uses OpenID4Java [http://code.google.com/p/openid4java/](http://code.google.com/p/openid4java/) to implement the feature.

OpenID is enabled by default in Liferay, but can be disabled here.

##### Atlassian Crowd [](id=lp-6-1-ugen12-atlassian-crowd-0)

Atlassian Crowd is a web-based Single Sign-On product similar to CAS. Crowd can be used to manage authentication to many different web applications and directory servers.

Because Atlassian Crowd implements an OpenID producer, Liferay works and has been tested with it. Simply use the OpenID authentication feature in Liferay to log in using Crowd.

##### Authentication: OpenSSO [](id=lp-6-1-ugen12-authentication-opensso-0)

OpenSSO is an open source single sign-on solution that comes from the code base of Sun's System Access Manager product. Liferay integrates with OpenSSO, allowing you to use OpenSSO to integrate Liferay into an infrastructure that contains a multitude of different authentication schemes against different repositories of identities.

You can set up OpenSSO on the same server as Liferay or a different box. Follow the instructions at the OpenSSO site [http://opensso.dev.java.net](http://opensso.dev.java.net/) to install OpenSSO. Once you have it installed, create the Liferay administrative user in it. Users are mapped back and forth by screen names. By default, the Liferay administrative user has a screen name of *test*, so in OpenSSO, you would register the user with the ID of *test* and an email address of *test@liferay.com*. Once you have the user set up, log in to Open SSO using this user.

In the same browser window, go to the URL for your server running Liferay and log in as the same user, using the email address *test@liferay.com*. Go to the control panel and click *Settings &rarr; Authentication &rarr; OpenSSO*. Modify the three URL fields (Login URL, Logout URL, and Service URL) so that they point to your OpenSSO server (i.e., only modify the host name portion of the URLs), click the *Enabled* check box, and then click *Save*. Liferay will then redirect users to OpenSSO when they click the *Sign In* link.

##### Authentication: SiteMinder [](id=lp-6-1-ugen12-authentication-siteminder-0)

SiteMinder is a single sign-on implementation from Computer Associates. Liferay 5.2 introduced built-in integration with SiteMinder. SiteMinder uses a custom HTTP header to implement its single sign-on solution.

To enable SiteMinder authentication in Liferay, check the *Enabled* box on the *SiteMinder* tab. If you are also using LDAP with Liferay, you can check the *Import from LDAP* box. If this box is checked, user authenticated from SiteMinder that do not exist in the portal will be imported from LDAP.

The last field defines the header SiteMinder is using to keep track of the user. The default value is already populated. If you have customized the field for your installation, enter the custom value here.

When you are finished, click *Save*. Next, let's examine how to configure portal-wide user settings.

#### Users [](id=lp-6-1-ugen12-users-0)

The Users page of Portal Settings has three tabs: Fields, Reserved Credentials, and Default User Associations.

The Fields tab allows you to enable/disable the following fields:

-   Enable/disable requiring the Terms of Use

-   Enable/disable user screen names autogeneration

-   Enable/disable requiring the last names

-   Enable/disable the birthday field

-   Enable/disable the gender field

The next tab is Reserved Credentials. You can enter screen names and email addresses here that you don't want others to use. Liferay will then prevent users from registering with these screen names and email addresses. You might use this feature to prevent users from creating IDs that look like administrative IDs or that have reserved words in their names.

The Default User Associations tab has three fields allowing you to list (one per line) sites, roles, and user groups that you want new users to become members of automatically. By default, Liferay assigns new users to both the Users role and the Power Users role.

If you have defined other user groups, sites, or roles that you want newly created users to be members of by default, enter them here. For example, you may have defined site templates in certain user groups to pre-populate end users' private pages. If there is a particular configuration that you want everyone to have, you may want to enter those user groups here.

#### Mail Host Names [](id=lp-6-1-ugen12-mail-host-names-0)

The next page under Portal Settings is Mail Host Names. You can enter (one per line) other mail host names besides the one you configured on the General tab. This lets the portal know which mail host names are owned by your organization.

#### Email Notifications [](id=lp-6-1-ugen12-email-notifications-0)

There are five tabs under the Email Notifications page of Portal Settings. The Sender tab allows you to set the portal's administrative name and email address. By default, these are `Joe Bloggs` and `test@liferay.com`. You can change them to whatever you want. This name and email address will appear in the From field in all email messages sent by the portal.

The other four tabs are Account Created Notification, Email Verification Notification, Password Changed Notification, and Password Reset Notification. These tabs allow you to customize the email messages that are sent to users each time any of those four events occur.

![Figure 12.22: Automated Emails: Account Created Notification](../../images/server-configuration-account-created-notification.png)

![Figure 12.23: Definition of Terms for Automated Emails](../../images/server-configuration-definition-of-terms.png)

A list of tokens, entitled "Definition of Terms," is provided so that you can insert certain values (such as the portal URL or the user ID) when you are setting up the custom email messages.

#### Identification [](id=lp-6-1-ugen12-identification-0)

The identification section has several links for addresses, phone numbers, and other information you can configure in your portal. This allows you to set up contact information for the organization that owns the portal. Developers can query for this information in their applications.

#### Miscellaneous: Display Settings [](id=lp-6-1-ugen12-miscellaneous-display-settings-0)

This section allows you to set the default portal language and the time zone. You can also set up a portal-wide logo which appears in the top left corners of portal pages. 

![Figure 12.24: Server Configuration Miscellaneous Display Settings](../../images/server-configuration-miscellaneous-display-settings.png)

Liferay's default theme is configured to display the portal logo. For custom themes, you can choose whether or not to display the logo. Be careful to choose an image file that fits the space. If you pick something that is too big, it might overlap with the navigation. Next, let's look at how to customize different types of portal assets using custom fields.

### Custom Fields [](id=lp-6-1-ugen12-custom-fields-0)

Custom fields are a way to add attributes to many types of assets in the portal. For example, if you're using Liferay Portal to create a site for rating books, you might assign the User object a custom field called Favorite Books. If you're using the wiki for book reviews, you might add fields for Book Title and Book Author.

To add a custom field, click on the *Custom Fields* link in the control panel. Then choose a resource, click on the *Edit* link next to it and select *Add Custom Field*.

![Figure 12.25: Custom Fields Resource List](../../images/server-configuration-custom-fields-resource-list.png)

From here you will need to add the custom field key. The key appears as the label for the field on the form. For some portal assets (like the User), custom fields are a separate section of the form. For others, as can be seen above, custom fields are integrated with the default fields on the form. Additionally, developers can access custom fields programatically through the `<liferay-ui:custom-attribute />` tag.

![Figure 12.26: Custom Fields Integrated with the Rest of the Fields on the Wiki Form](../../images/server-configuration-custom-fields-integrated.png)

You can create fields of many different types: text fields (indexed or secret), integers, selection of multiple values, and more. Once you've created a field, you cannot change its type.

### Monitoring [](id=lp-6-1-ugen12-monitoring-0)

The next link on the left side of the control panel is for monitoring. You can use the Monitoring page to view all of the live sessions in the portal. For performance reasons, this setting is usually turned off in production.

### Plugins Configuration [](id=lp-6-1-ugen12-plugins-configuration-0)

The Plugins Configuration page contains tabs for three types of plugins: portlets, themes, and layouts. You can use these tabs to view which roles can add plugins to pages or you can make the plugins active or inactive.

Note that this is for basic configuration: if you want to view the existing permission configuration for a given portlet and/or modify that configuration for existing roles, this is where you can do that. If you need to add permissions to new roles for a given portlet, use the Roles section of the control panel and the *Actions &rarr; Define Permissions* button. Next, let's look at how to apply server configurations.

### Server Administration [](id=lp-6-1-ugen12-server-administration-0)

The Server Administration page of the control panel lets you perform various tasks related to the portal server itself, as opposed to the resources in the portal. Clicking the link makes this clear: you're immediately presented with a graph showing the resources available in the JVM.

#### Resources [](id=lp-6-1-ugen12-resources-0)

The first tab is called *Resources* . This tab contains the aforementioned graph plus several server wide actions that an administrator can execute. These are:

**Garbage collection:** You can send in a request to the JVM to begin the garbage collection task.

**Clearing VM caches:** You can send in a request to the JVM to clear a single VM cache.

**Clearing caches across the cluster:** You can send in a request to the JVM to clear content cached across the entire cluster.

**Clearing database caches:** You can send in a request to the JVM to clear the database cache.

**Reindex all search indexes:** You can send in a request to regenerate all search indexes. If you are not using a Solr search server this will impact portal performance, so try not to do this except at non-peak times.

**Reset Document Library preview and thumbnail files:** You can send in a request to reset the preview and thumbnail files for each item in your portal's Documents and Media libraries.

**Generate Thread Dump:** If you are performance testing, you can generate a thread dump which can be examined later to determine if there are any deadlocks and where they might be.

**Verify database tables of all plugins:** Checks all tables against their indexes for accuracy of data retrieval.

**Clean up Permissions:** This process removes the assignment of some permissions on the Guest, User and Power User roles in order to simplify the management of "User Customizable Pages". Notably, "Add To Page" permissions is removed from the Guest, and User role for all portlets. Likewise the same permission is reduced in scope for Power Users from portal wide to scoped to "User Personal Site".

#### Log Levels [](id=lp-6-1-ugen12-log-levels-0)

The Log Levels tab of the Server Administration page allows you to dynamically modify the log levels for any class hierarchy in the portal. If you have custom code that you have deployed which isn't in the list, you can use the *Add Category* tab to add it. If you change the log level near the top of the class hierarchy (such as at `com.liferay`), all the classes under that hierarchy will have their log levels changed. If you are testing something specific, it is much better to be as specific as you can when you change log levels. Modifying them too high in the hierarchy generates a lot more log messages than you need.

#### Properties [](id=lp-6-1-ugen12-properties-0)

Liferay and the JVM contain many settings which are defined as properties. There are two subtabs of the properties tab of the Server Administration page: one showing system properties and one showing portal properties.

The system properties tab shows an exhaustive list of system properties for the JVM, as well as many Liferay system properties. This information can be used for debugging purposes or to check the configuration of the currently running portal.

The portal properties tab tab shows an exhaustive list of the portal properties. These properties can be customized, as we saw in chapter 12. If you need to check the current value of a particular property, it can be viewed from this screen without having to shut down the portal or open any properties files.

#### Captcha [](id=lp-6-1-ugen12-captcha-0)

By default, Liferay ships with its own simple captcha service which is designed to thwart bots from registering for accounts on sites powered by Liferay. If you want to instead use Google's reCaptcha service, you can enable this setting from the Captcha tab of the Server Administration page.

Simply check the *Enable ReCaptcha* box and enter your public and private keys into the provided fields, and then click *Save*. Liferay Portal will then use reCaptcha instead of simple captcha.

#### Data Migration [](id=lp-6-1-ugen12-data-migration-0)

If you are upgrading from a previous release of Liferay Portal or if you need to migrate your data from one system to another, the Data Migration tab helps you to do that without your developers having to write custom scripts.

The first section lets you copy your entire Liferay database from the current database under which it is running to the database you specify in this set of fields. You'll need to enter the driver class name (and the driver will need to be on Liferay's classpath), the JDBC URL of the database to which you'll be copying your data, and the credentials of a user that has access to that database. Once you have all of this information entered, click *Execute* to copy the data.

The next section helps you migrate your documents. If you want to move off of the Jackrabbit JSR-170 repository to the file system, or to the Jackrabbit repository from the file system, or to any of the other repositories supported by the documents and media library, you can do so very easily. Make sure you have already set up your `portal-ext.properties` file so that the hook is properly configured before running this migration. Select the Document Library hook that represents where you want your documents migrated, and click *Execute*. Your documents will be migrated to the new repository, and you can then shut down Liferay, make the new repository the default in the `portal-ext.properties` file, and then restart.

Similarly, you can migrate images from the Image Gallery in the same manner.

#### File Uploads [](id=lp-6-1-ugen12-file-uploads-0)

Since Liferay allows users to upload files in various places, you may want to lock down the type of files and the size of files users are allowed to upload. The File Uploads tab of the Server Configuration tab lets you set the overall maximum file size and then override that size for specific applications within Liferay. You can limit the allowed file extensions generally or by application. You have a lot of flexibility as to how you want files to be managed within your portal.

#### Mail [](id=lp-6-1-ugen12-mail-0)

Rather than using the `portal-ext.properties` file as we did in the installation chapter, you can configure a mail server from the Mail tab of the Server Configuration tab. If the portal is to receive mail (see the Message Boards portlet in Chapter 4), you can connect a POP mail server. If the portal is to send mail, which it needs to do in order to send notifications to users, you can connect to an SMTP server here as well, and this is highly recommended.

Note that if you add your mail server settings here, they will override anything that is in your `portal-ext.properties` file.

#### External Services [](id=lp-6-1-ugen12-external-services-0)

Liferay Portal enables users to add content in many formats: web content, images, and files. This is done using the Web Content Management System, the Image Gallery, the Documents and Media Library, and in other portlets, both built-in and custom written. Sometimes, it is helpful to convert this content from its original format to one that is more convenient for the user browsing the content. Liferay Portal allows users to do this by integrating with OpenOffice and Xuggler.

OpenOffice is an open source office suite which usually runs in graphical mode to create documents, but it can also be run in "server" mode. When run in server mode, OpenOffice can be used to convert documents to and from all of the file types it supports. Liferay can then make use of this feature to automatically convert content on the fly. Xuggler provides video conversion functionality.

Use the External Services tab to tell Liferay how to connect to your running instance of OpenOffice or Xuggler. You can install OpenOffice on the same server upon which Liferay is running. Once you have it installed, you can start OpenOffice in server mode with the following command:

    soffice -headless -accept="socket,host=127.0.0.1,port=8100;urp;"
    -nofirststartwizard

As you can see, the command above specifies that OpenOffice will run on port 8100, which is the default port in the control panel . If you can use this port, all you need to do is check the *Enabled* box, and Liferay will be integrated with OpenOffice.

If you have something else running on this port, find a port that is open and specify it both in the command above and on the control panel's External Services configuration page. When you are finished, click *Save*.

#### Script [](id=lp-6-1-ugen12-script-0)

Liferay includes a scripting console which lets administrators execute migration or management code instantly. Several scripting languages are supported, including JavaScript, Groovy, Python, Ruby, and Beanshell. For further information about Liferay's APIs, see the JavaDoc, the Liferay Wiki ([http://wiki.liferay.com](http://wiki.liferay.com/)), or [*Liferay in Action*](http://manning.com/sezov).

#### Shutdown [](id=lp-6-1-ugen12-shutdown-0)

If you ever need to shut down your Liferay Portal server while users are logged in, you can use the Shutdown tab to inform your logged-in users of the impending shutdown. You can define the number of minutes until the shutdown and a custom message that will be displayed.

Users will see your message at the top of their portal pages for the duration of time you specified. When the time expires, all portal pages will display a message saying the portal has been shut down. At this point, the server will need to be restarted to restore access. Next, let's examine how to manage multiple portal instances.

### Portal Instances [](id=lp-6-1-ugen12-portal-instances-0)

Liferay Portal allows you to run more than one portal instance on a single server. The Portal Instances page of the control panel lets you manage these instances. Data for each portal instance are kept separate from every other portal instance. All portal data, however, is kept in the same database.

Each portal instance requires its own domain name. Liferay will direct users to the proper portal instance based on this domain name. So before you configure an instance, configure its domain name in your network first. When you're ready to add an instance, click the *Add* button here.

You'll be prompted for four fields and a check box:

**Web ID:** A general convention is to use the domain name for this. It's a user-generated ID for the instance.

**Virtual Host:** Put the domain name you configured in your network here. When **users** are directed to your Liferay server via this domain name, Liferay will then be able to send them to the proper portal instance.

**Mail Domain:** Enter the domain name for the mail host for this instance. Liferay will use this to send email notifications from the portal.

**Max Users:** Enter the maximum numbers of user accounts you would like your portal instance to support.

**Active:** Use this check box to choose whether to create an active or an inactive portal instance.

When you are finished filling out the form, click *Save*. Now navigate to the portal using your new domain name. You will see that you are brought to what looks like a clean install of Liferay. This is your new portal instance which can now be configured any way you like.

### Plugins Installation [](id=lp-6-1-ugen12-plugins-installation-0)

The *Plugins Installation* page of the control panel shows all of the plugins that are currently installed. These are divided into tabs for portlets, themes, layout templates, hook plugins, and web plugins. If you want to install a new plugin, click the *Install More Portlets* button. You will then be brought to the Plugin Installer, where you can browse Liferay's repository of portlets or install your own plugins. We covered the plugins installer in chapter 2.

## Summary [](id=summ-33)

In this chapter we described how to use Liferay's control panel to manage users, user groups, organizations, sites, and roles. We showed how to configure various server settings, such as authentication, LDAP integration, and single sign-on. We also learned how to associate users by default with different user groups, sites, and roles, and we saw how to reserve screen names and email addresses so that users cannot register in the portal with them.

Next, we saw how to view and configure overall server settings. We saw how to view the memory currently being used by the server, as well as how to initiate garbage collection, a thread dump, search engine re-indexing, and the clearing of various caches. We learned how to debug parts of the portal by changing log levels, and by viewing the various properties that are defined in the portal.

Finally, we learned how to properly notify users that the portal is about to shut down and how to set up exernal services like OpenOffice integration. We looked at how to create multiple portal instances on a single installation of Liferay and we showed how to view currently installed plugins.

We hope this information helps you become an effective Liferay Portal Administrator.

