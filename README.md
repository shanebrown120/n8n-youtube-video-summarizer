# YouTube Caption Summarizer Workflow

## Overview

This n8n workflow automatically pulls the latest videos from your favorite YouTube channel, scrapes and cleans their captions, summarizes them using Google Gemini’s AI, and sends the summary via Telegram.

***

## Workflow Steps

- **RSS Node:** Polls your chosen YouTube channel every 30–60 minutes for new videos. Setting a polling interval of at least 30 minutes is recommended, as YouTube captions may not be immediately available after a video is posted.
- **Remove Duplicate Node:** Prevents redundant summaries by checking if a video has already been processed. Only new videos proceed further in the workflow.
- **HTTP Request Node (Apify):** Scrapes YouTube captions using Apify’s 'Youtube Transcripts' actor (`karamelo/youtube-transcripts`). With a free Apify account, you get ~$5 credit monthly, enough for ~714 transcripts.
- **Code Node:** Cleans up the scraped captions for better grammar, punctuation, and readability before summarization.
- **AI Agent Node:** Processes cleaned captions via Google Gemini’s chat model (free) and generates a concise summary.
- **Telegram Node:** Sends the AI-generated summary directly to you in Telegram for quick updates on new content.

***

## Setup Instructions

1. **Install n8n**: Use Docker or your preferred method.
2. **Import Workflow**: Download the provided JSON file and import it via n8n’s workflow editor.
3. **Configure Nodes**:
   - Set up your preferred YouTube channel RSS feed.
   - Enter Apify credentials and subscribe to the 'Youtube Transcripts' actor.
   - Provide your Telegram bot token and user ID.
4. **Customize Schedule**: Adjust the polling interval to fit your needs (recommend 30–60 minutes).
5. **Run & Receive Summaries**: Enable the workflow. You’ll receive a Telegram summary shortly after a new video is posted.

***

## Notes

- Captions may not be available immediately after a video is uploaded; poll at reasonable intervals to ensure summaries include accurate captions.
- Apify usage beyond 714 transcripts/month may incur additional costs.
- Contributions and suggestions are welcome. Please open an issue or pull request for improvements.
