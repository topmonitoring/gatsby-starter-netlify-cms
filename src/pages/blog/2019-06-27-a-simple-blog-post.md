---
templateKey: blog-post
title: 'A simple blog post '
date: 2019-06-26T21:17:57.067Z
description: a random generated first blog post of all time
featuredpost: false
featuredimage: /img/62241128_2349143021787604_8166901427403227136_n.jpg
tags:
  - starter new blog post
---
Netlify CMS will need to authenticate with GitHub to save your content changes to your repo. As mentioned above, this requires a server, and Netlify handles that aspect for you. First you’ll need to add your deployed site as an OAuth application in your GitHub settings - just follow the steps in the Netlify docs. This will allow scripts running on your deployed site, such as Netlify CMS, to access your GitHub account via API.



Lastly, we’ll need to change your Netlify CMS config file with your GitHub repo information so that changes are saved there. Replace the backend value in your static/admin/config.yml to match the example below. Note that the repo value must be your GitHub username followed immediately by a forward slash, and then your repository name. If your username is “test-user” and your repo name is “test-repo”, you would put “test-user/test-repo”.



static/admin/config.yml

backend:

  name: github

  repo: your-username/your-repo-name

Now you can save the config.yml file, commit the change, and push it to your GitHub repo.



Authenticating with GitLab

See the GitLab Backend section for details on how to configure authentication with GitLab.



If you use the Client-Side Implicit Grant option, disable the Netlify Identity service in your gatsby-config.js:



gatsby-config.js

{

  resolve: \`gatsby-plugin-netlify-cms\`,

  options: {

\    enableIdentityWidget: false,

  }

}

Making Changes

Alright - you’re all set to make changes in Netlify CMS and see them as commits in your GitHub repo! Open Netlify CMS on your deployed site at /admin/, allow access to GitHub when the permissions window pops up (check for blocked pop ups if you don’t see it), and try creating and publishing a new blog post. Once you’ve done that, you’ll find a new “blog” directory in your GitHub repo containing a Markdown file with your blog post content!



This is the basic function of Netlify CMS - providing a comfortable editing experience and outputting raw content files to a Git repository. You’ve probably noticed that, even though the file was created in your repo, it’s not anywhere on your site. That’s because Netlify CMS doesn’t go beyond creating the raw content - it’s able to work with almost any static site generator because it allows the generator to determine how to build the raw content into something useful, whether for a website, mobile app, or something else entirely.



Right now, Gatsby doesn’t know the new blog post is there, and it isn’t set up to process Markdown. Let’s fix that.



Processing Netlify CMS Output with Gatsby

Gatsby can be configured to process Markdown by following the Adding Markdown Pages guide in the docs. Our config.yml file for Netlify CMS is set up to use the same fields used in the guide, so you can follow the instructions to the letter and should work fine. Note: When configuring the gatsby-source-filesystem plugin in the Adding Markdown Pages Guide, the path to your markdown files should be ${__dirname}/blog.



Once this is complete, get your changes committed and pushed up to your GitHub repo and check your site! The new blog post will be at whatever you entered in the path field when creating your blog entry in Netlify CMS. If you followed the example in Gatsby’s Adding Markdown Pages guide and used “/blog/my-first-blog”, then your blog post would be at “your-site-name.netlify.com/blog/my-first-blog”.



Wrapping Up

This was a very basic example meant to help you understand how Netlify CMS works with Gatsby. As mentioned in the beginning of this guide, if you got stuck, you can compare your code to the example repo, which is a working example created by following this guide. You can also reach out to the Netlify CMS community on Gitter. Lastly, if you’d like to move into a more complete boilerplate to get going with Gatsby
