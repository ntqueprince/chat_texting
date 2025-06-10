<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SHIVANG</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap" rel="stylesheet">
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    body {
      font-family: 'Poppins', sans-serif;
      padding: 20px;
      background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%);
      text-align: center;
      margin: 0;
      min-height: 100vh;
    }
    h2, h3 {
      color: #1a237e;
      font-weight: 600;
    }
    h2 {
      font-size: 2em;
      letter-spacing: 1px;
    }
    h3 {
      font-size: 1.5em;
    }
    .upload-section {
      margin-top: 20px;
      margin-bottom: 20px;
      background: rgba(255, 255, 255, 0.9);
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    }
    input[type="file"], input[type="text"], button {
      padding: 12px;
      margin: 8px;
      font-size: 16px;
      border-radius: 8px;
      border: 1px solid #b0bec5;
      width: 80%;
      max-width: 300px;
      box-sizing: border-box;
      transition: all 0.3s ease;
    }
    input[type="text"]:focus, input[type="file"]:focus {
      border-color: #3f51b5;
      box-shadow: 0 0 8px rgba(63, 81, 181, 0.3);
      outline: none;
    }
    button {
      background-color: #3f51b5;
      color: white;
      border: none;
      cursor: pointer;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
    }
    button:hover {
      background-color: #303f9f;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
      transform: translateY(-2px);
    }
    .progress-container {
      width: 80%;
      max-width: 300px;
      margin: 10px auto;
    }
    .progress-bar {
      width: 100%;
      background-color: #eceff1;
      border-radius: 8px;
      overflow: hidden;
    }
    .progress {
      width: 0%;
      height: 20px;
      background: linear-gradient(90deg, #3f51b5, #5c6bc0);
      text-align: center;
      line-height: 20px;
      color: white;
      font-weight: 400;
      transition: width 0.3s ease;
    }
    .status {
      margin-top: 5px;
      font-size: 14px;
      color: #455a64;
      font-weight: 400;
    }
    #gallery {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 15px;
      justify-items: center;
      padding: 10px;
    }
    .image-container {
      background: white;
      padding: 10px;
      border-radius: 12px;
      box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
      text-align: center;
      transition: all 0.3s ease;
      max-width: 200px;
      position: relative;
      overflow: hidden;
    }
    .image-container:hover {
      transform: translateY(-5px);
      box-shadow: 0 6px 15px rgba(0, 0, 0, 0.15);
    }
    #gallery img {
      max-width: 100%;
      height: 150px;
      object-fit: cover;
      border-radius: 8px;
      border: 2px solid #e0e0e0;
      transition: all 0.3s ease;
    }
    .image-container:hover img {
        filter: brightness(70%);
    }
    .tag {
      margin: 5px 0;
      font-size: 16px;
      font-weight: 500;
      color: #37474f;
    }
    /* Styles for Download Button */
    .download-btn {
      background-color: #ff5722;
      color: white;
      padding: 8px 12px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-size: 14px;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      transition: opacity 0.3s ease, transform 0.3s ease;
      text-decoration: none;
      white-space: nowrap;

      position: absolute;
      bottom: 10px;
      left: 50%;
      transform: translateX(-50%);
      opacity: 0;
      visibility: hidden;
    }
    .image-container:hover .download-btn {
      opacity: 1;
      visibility: visible;
    }
    .download-btn:hover {
      background-color: #e64a19;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
      transform: translateX(-50%) translateY(-2px);
    }
    /* Popup Styles for Tag Modal */
    .modal {
      display: none;
      position: fixed;
      z-index: 1;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.6);
      justify-content: center;
      align-items: center;
    }
    .modal-content {
      background-color: white;
      padding: 25px;
      border-radius: 15px;
      box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
      width: 90%;
      max-width: 400px;
      text-align: center;
      border: 2px solid #3f51b5;
    }
    .modal-content h4 {
      margin: 0 0 15px;
      color: #d32f2f;
      font-weight: 500;
    }
    .modal-content input[type="text"] {
      width: 100%;
      padding: 10px;
      margin-bottom: 15px;
      border: 1px solid #b0bec5;
      border-radius: 8px;
      transition: all 0.3s ease;
    }
    .modal-content input[type="text"]:focus {
      border-color: #3f51b5;
      box-shadow: 0 0 8px rgba(63, 81, 181, 0.3);
      outline: none;
    }
    .modal-content button {
      padding: 10px 20px;
      margin: 5px;
      border-radius: 8px;
      cursor: pointer;
    }
    .modal-content .upload-btn {
      background-color: #3f51b5;
      color: white;
      border: none;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    }
    .modal-content .upload-btn:hover {
      background-color: #303f9f;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    }
    .modal-content .cancel-btn {
      background-color: #f44336;
      color: white;
      border: none;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    }
    .modal-content .cancel-btn:hover {
      background-color: #d32f2f;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    }
    .modal-progress-container {
      width: 100%;
      margin: 10px 0;
      display: none;
    }
    .modal-progress-bar {
      width: 100%;
      background-color: #eceff1;
      border-radius: 8px;
      overflow: hidden;
    }
    .modal-progress {
      width: 0%;
      height: 20px;
      background: linear-gradient(90deg, #3f51b5, #5c6bc0);
      text-align: center;
      line-height: 20px;
      color: white;
      font-weight: 400;
      transition: width 0.3s ease;
    }
    /* CSAT Calculator Modal Styles */
    .csat-modal {
      display: none;
      position: fixed;
      z-index: 2;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.6);
      justify-content: center;
      align-items: center;
    }
    .csat-modal-content {
      background-color: white;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
      width: 90%;
      max-width: 400px;
      text-align: center;
      border: 2px solid #3f51b5;
    }
    .csat-modal-content h4 {
      color: #1a237e;
      font-weight: 600;
      margin-bottom: 15px;
    }
    .csat-modal-content .input-section {
      margin-bottom: 15px;
    }
    .csat-modal-content label {
      display: block;
      font-size: 1em;
      color: #37474f;
      margin-bottom: 5px;
    }
    .csat-modal-content input, .csat-modal-content select {
      padding: 10px;
      font-size: 1em;
      border-radius: 8px;
      border: 1px solid #b0bec5;
      width: 100%;
      max-width: 200px;
      box-sizing: border-box;
      transition: all 0.3s ease;
    }
    .csat-modal-content input:focus, .csat-modal-content select:focus {
      border-color: #3f51b5;
      box-shadow: 0 0 8px rgba(63, 81, 181, 0.3);
      outline: none;
    }
    .csat-modal-content .good-section {
      background: #c8e6c9;
      padding: 10px;
      border-radius: 8px;
    }
    .csat-modal-content .bad-section {
      background: #ffcdd2;
      padding: 10px;
      border-radius: 8px;
    }
    .csat-modal-content .result-section {
      margin-top: 15px;
      padding: 10px;
      background: #eceff1;
      border-radius: 8px;
    }
    .csat-modal-content .result-section p {
      margin: 5px 0;
      font-size: 0.9em;
      color: #455a64;
    }
    .csat-modal-content .success {
      color: #2e7d32;
      font-weight: 500;
      padding: 5px;
      border-radius: 4px;
      background: rgba(200, 230, 201, 0.3);
    }
    .csat-modal-content .error {
      color: #c62828;
      font-weight: 600;
      font-size: 1em;
      padding: 5px;
      border-radius: 4px;
      background: rgba(255, 205, 210, 0.3);
      display: inline-block;
    }
    /* Button container for "Close" and "Calculate" */
    .csat-modal-content .button-container {
      display: flex;
      justify-content: center;
      gap: 15px;
      margin-top: 20px;
      flex-wrap: wrap;
    }
    .csat-modal-content .button-container button {
      flex: 1;
      max-width: 150px;
      margin: 0;
    }

    .csat-modal-content .close-btn {
      background-color: #f44336;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 8px;
      cursor: pointer;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
    }
    .csat-modal-content .close-btn:hover {
      background-color: #d32f2f;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    }
    .csat-modal-content .calculate-btn {
      background-color: #3f51b5;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 8px;
      cursor: pointer;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
    }
    .csat-modal-content .calculate-btn:hover {
      background-color: #303f9f;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    }
    /* Fixed Buttons */
    .csat-btn, .endorsement-btn, .manual-vi-btn-fixed, .claim-count-nstp-btn-fixed {
      position: fixed;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 8px;
      cursor: pointer;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
      font-size: 0.9em;
      display: block;
    }

    .csat-btn {
      top: 10px;
      left: 10px;
      background-color: #1b5e20;
    }
    .csat-btn:hover {
      background-color: #2e7d32;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
      transform: translateY(-2px);
    }

    .endorsement-btn {
      top: 10px;
      right: 10px;
      background-color: #1b5e20;
    }
    .endorsement-btn:hover {
      background-color: #2e7d32;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
      transform: translateY(-2px);
    }

    .manual-vi-btn-fixed {
        top: 60px;
        right: 10px;
        background-color: #3f51b5;
    }

    .manual-vi-btn-fixed:hover {
      background-color: #303f9f;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
      transform: translateY(-2px);
    }

    .claim-count-nstp-btn-fixed {
        top: 60px;
        left: 10px;
        background-color: #3f51b5;
    }
    .claim-count-nstp-btn-fixed:hover {
        background-color: #303f9f;
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        transform: translateY(-2px);
    }

    /* ENDORSEMENT Full-Page Widget Styles */
    .endorsement-page {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%);
      z-index: 1000;
      padding: 0;
      margin: 0;
      box-sizing: border-box;
      font-family: 'Roboto', sans-serif;
      overflow-y: auto;
    }
    .endorsement-container {
      width: 100%;
      max-width: 600px;
      margin: 0 auto;
      background: #ffffff;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
      transition: transform 0.3s ease, opacity 0.3s ease;
      transform: scale(0.9);
      opacity: 0;
      position: relative;
      top: 50%;
      transform: translateY(-50%);
    }
    .endorsement-container.active {
      transform: scale(1) translateY(-50%);
      opacity: 1;
    }
    .endorsement-container h1 {
      text-align: center;
      color: #1a237e;
      font-size: 1.8em;
      font-weight: 700;
      margin-bottom: 8px;
    }
    .created-by {
      text-align: center;
      font-size: 0.8em;
      margin-bottom: 15px;
      background: linear-gradient(90deg, #3f51b5, #e91e63);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      animation: fadeIn 1.5s ease-in-out;
    }
    @keyframes fadeIn {
      0% { opacity: 0; transform: translateY(10px); }
      100% { opacity: 1; transform: translateY(0); }
    }
    .endorsement-container label {
      display: block;
      color: #263238;
      font-size: 1em;
      font-weight: 500;
      margin: 10px 0 6px;
    }
    .PB_DROPDOWN {
      width: 100%;
      padding: 10px;
      border: 2px solid #b0bec5;
      border-radius: 8px;
      font-size: 0.95em;
      font-family: Arial, Helvetica, sans-serif;
      background: #fafafa;
      transition: border-color 0.3s ease, box-shadow 0.3s ease;
      cursor: pointer;
      height: 40px;
      appearance: none;
      -webkit-appearance: none;
      -moz-appearance: none;
      background-image: url('data:image/svg+xml;utf8,<svg fill="black" height="24" viewBox="0 0 24 24" width="24" xmlns="http://www.w3.org/2000/svg"><path d="M7 10l5 5 5-5z"/></svg>');
      background-repeat: no-repeat;
      background-position: right 10px center;
    }
    .PB_DROPDOWN:focus {
      outline: none;
      border-color: #3f51b5;
      box-shadow: 0 0 8px rgba(63, 81, 181, 0.3);
    }
    .PB_DROPDOWN:hover {
      border-color: #3f51b5;
    }
    .output {
      background: #e3f2fd;
      padding: 15px;
      border-radius: 10px;
      margin-top: 15px;
      font-size: 1em;
      font-weight: 500;
      line-height: 1.6;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
      border: 1px solid #bbdefb;
      transform: scale(0.95);
      opacity: 0;
      transition: transform 0.3s ease, opacity 0.3s ease;
    }
    .output.show {
      transform: scale(1);
      opacity: 1;
    }
    .output.output-red {
      background: #f8d7da;
      border: 1px solid #f5c6cb;
    }
    .output div {
      margin-bottom: 8px;
    }
    .label {
      color: #1565c0;
      font-weight: 700;
      margin-right: 8px;
    }
    .output-red .label {
      color: #721c24;
    }
    .value {
      color: #263238;
    }
    .back-btn {
      background-color: #f44336;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 8px;
      cursor: pointer;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
      margin-top: 15px;
      display: block;
      margin-left: auto;
      margin-right: auto;
    }
    .back-btn:hover {
      background-color: #d32f2f;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
      transform: translateY(-2px);
    }
    /* Styles for Manual VI Page */
    .manual-vi-page {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%);
      z-index: 1000;
      padding: 20px;
      box-sizing: border-box;
      text-align: center;
      overflow-y: auto;
    }
    .manual-vi-page .back-to-home-btn {
      display: none;
    }
    .manual-vi-page .card {
        margin-top: 100px;
    }
    .manual-vi-page .card-header {
      background-color: #343a40 !important;
      color: white !important;
      padding: 10px 15px;
      border-top-left-radius: 15px;
      border-top-right-radius: 15px;
      font-weight: 600;
    }
    .manual-vi-page .card-body {
      padding: 20px;
    }
    .manual-vi-page ul {
      list-style-type: disc;
      padding-left: 20px;
      text-align: left;
      padding-top: 20px;
    }

    /* Styles for Claim_Count & NSTP Page (Insurance Comparison Dashboard) */
    .claim-count-nstp-page {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%);
      z-index: 1000;
      padding: 20px;
      box-sizing: border-box;
      overflow-y: auto;
      font-family: 'Poppins', sans-serif;
    }
    .claim-count-nstp-page .table-header {
        cursor: pointer;
        transition: background-color 0.3s, transform 0.2s;
        background-color: #2d3748;
        color: white;
    }
    .claim-count-nstp-page .table-header:hover {
        background-color: #4a5568;
        transform: scale(1.03);
    }
    .claim-count-nstp-page .sort-icon::after {
        content: '↕';
        margin-left: 5px;
        display: inline-block;
        color: white;
    }
    .claim-count-nstp-page .sort-asc::after {
        content: '↑';
        color: white;
    }
    .claim-count-nstp-page .sort-desc::after {
        content: '↓';
        color: white;
    }
    .claim-count-nstp-page .table-row {
        transition: background-color 0.3s;
    }
    .claim-count-nstp-page .table-row:hover {
        background-color: #fefcbf;
    }
    .claim-count-nstp-page .search-input {
        transition: all 0.3s;
    }
    .claim-count-nstp-page .search-input:focus {
        border-color: #db2777;
        box-shadow: 0 0 10px rgba(219, 39, 119, 0.5);
    }
    .claim-count-nstp-page td, .claim-count-nstp-page th {
        white-space: normal !important;
        word-break: break-words !important;
    }
    .claim-count-nstp-page .table-row:nth-child(odd) {
        background-color: #e0f7fa;
    }
    .claim-count-nstp-page .table-row:nth-child(even) {
        background-color: #fce4ec;
    }
    .claim-count-nstp-page .table-row:hover {
        background-color: #fff9c4 !important;
    }

    /* Chatbox button */
    .chatbox-toggle-btn {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background-color: #e91e63;
      color: white;
      border: none;
      border-radius: 50%;
      width: 60px;
      height: 60px;
      font-size: 2em;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
      z-index: 9999;
      transition: all 0.3s ease;
    }

    .chatbox-toggle-btn:hover {
      background-color: #c2185b;
      transform: scale(1.05);
    }

    /* Chatbox Container - Full page overlay */
    .chatbox-container {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.7);
      z-index: 9998;
      justify-content: center;
      align-items: center;
    }

    /* Chatbox Content - The actual chat window */
    .chatbox-content {
      width: 90%;
      max-width: 500px;
      height: 90%;
      max-height: 600px;
      background-color: white;
      border-radius: 15px;
      box-shadow: 0 5px 25px rgba(0, 0, 0, 0.5);
      display: flex;
      flex-direction: column;
      overflow: hidden;
      border: 1px solid #e0e0e0;
    }

    .chatbox-header {
      background-color: #3f51b5;
      color: white;
      padding: 15px;
      border-top-left-radius: 15px;
      border-top-right-radius: 15px;
      font-size: 1.2em;
      font-weight: 600;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      position: relative;
    }

    .chatbox-header .chatbox-title {
        font-size: 1.2em;
        font-weight: 600;
        margin-bottom: 2px;
    }

    .chatbox-header .chatbox-subtitle {
        font-size: 0.65em; /* Even smaller font for shivang */
        font-weight: 300; /* Even lighter font weight for shivang */
        color: rgba(255, 255, 255, 0.4); /* Even less prominent color for shivang */
    }

    /* .chatbox-header .close-chat { display: none; } Removed from HTML directly */

    .chatbox-messages {
      flex-grow: 1;
      padding: 15px;
      overflow-y: auto;
      background-color: #f0f4f7;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .chatbox-message {
      padding: 10px 12px;
      border-radius: 12px;
      max-width: 85%;
      word-wrap: break-word;
      font-size: 0.95em;
      line-height: 1.4;
      box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
      position: relative;
      color: white; /* Default to white text for all messages */
    }

    .chatbox-message .reply-text-preview {
        font-size: 0.8em;
        opacity: 0.7;
        margin-bottom: 5px;
        padding-bottom: 3px;
        display: block;
        font-style: italic;
    }

    /* Message colors - Dark tones for main messages */
    .message-primary-dark {
      background-color: #1a237e; /* Deep Blue */
    }
    .message-secondary-dark {
      background-color: #ff5722; /* Deep Orange */
    }

    /* Reply colors - Lighter tones with borders */
    .message-primary-reply {
      background-color: #a7b7e5; /* Lighter blue for replies */
      color: white; /* Ensure text is visible */
    }
    .message-secondary-reply {
      background-color: #ffddc1; /* Lighter orange for replies */
      color: white; /* Ensure text is visible */
    }

    /* Alignment specific styles */
    .align-right {
        align-self: flex-end;
        border-bottom-left-radius: 12px;
        border-bottom-right-radius: 3px;
    }
    .align-left {
        align-self: flex-start;
        border-bottom-right-radius: 12px;
        border-bottom-left-radius: 3px;
    }

    /* Reply specific margins and borders */
    /* This style will be applied dynamically based on parent's color */
    .chatbox-message.is-reply {
      padding-left: 10px; /* Adjust padding due to border */
      padding-right: 10px;
      margin-left: 20px; /* Indent for replies */
      margin-right: 20px; /* Indent for replies */
      border-width: 5px;
      border-style: solid;
    }

    .chatbox-input-area {
      display: flex;
      padding: 15px;
      border-top: 1px solid #e0e0e0;
      background-color: #fcfcfc;
    }

    .chatbox-input-area input {
      flex-grow: 1;
      padding: 10px 15px;
      border: 1px solid #b0bec5;
      border-radius: 20px;
      font-size: 1em;
      margin-right: 10px;
      outline: none;
      transition: border-color 0.3s ease;
    }

    .chatbox-input-area input:focus {
      border-color: #3f51b5;
    }

    .chatbox-input-area button {
      background-color: #3f51b5;
      color: white;
      border: none;
      border-radius: 20px;
      padding: 10px 20px;
      cursor: pointer;
      font-size: 1em;
      transition: background-color 0.3s ease;
    }

    .chatbox-input-area button:hover {
      background-color: #303f9f;
    }

    /* Reply button on messages */
    .reply-btn {
        position: absolute;
        bottom: 5px;
        right: 5px;
        background: rgba(255, 255, 255, 0.2);
        color: white;
        border: none;
        border-radius: 50%;
        width: 24px;
        height: 24px;
        font-size: 0.7em;
        display: flex;
        justify-content: center;
        align-items: center;
        cursor: pointer;
        opacity: 0;
        transition: opacity 0.2s ease;
    }

    .chatbox-message:hover .reply-btn {
        opacity: 1;
    }


    /* Media Queries for Chatbox on smaller screens */
    @media (max-width: 600px) {
      .csat-btn,
      .endorsement-btn,
      .manual-vi-btn-fixed,
      .claim-count-nstp-btn-fixed {
        display: none;
      }

      body {
        padding-top: 20px;
      }

      #gallery {
        grid-template-columns: 1fr;
      }
      .image-container {
        padding: 8px;
        max-width: 100%;
      }
      h2, h3 {
        font-size: 1.2em;
      }
      .modal-content, .csat-modal-content {
        width: 80%;
        padding: 15px;
      }
      .csat-modal-content .error {
        font-size: 0.85em;
        padding: 4px;
      }
      .csat-modal-content .success {
        font-size: 0.85em;
        padding: 4px;
      }
      .csat-modal-content .result-section p {
        font-size: 0.8em;
      }
      .endorsement-container {
        width: 90vw;
        padding: 15px;
      }
      .endorsement-container h1 {
        font-size: 1.5em;
      }
      .PB_DROPDOWN {
        font-size: 0.9em;
        height: 36px;
      }
      .output {
        font-size: 0.95em;
      }
      .created-by {
        font-size: 0.7em;
      }
      .manual-vi-page .card, .claim-count-nstp-page .container {
        margin-top: 60px;
      }
      .claim-count-nstp-page h1 {
        font-size: 1.8em;
      }
      .endorsement-page .back-btn,
      .manual-vi-page .back-to-home-btn,
      .claim-count-nstp-page .back-btn {
        display: block;
        position: absolute;
        top: 20px;
        left: 20px;
        z-index: 1001;
      }

      .chatbox-content {
        width: 95vw;
        height: 95vh;
        max-width: unset;
        max-height: unset;
      }
      .chatbox-toggle-btn {
        width: 50px;
        height: 50px;
        font-size: 1.8em;
        bottom: 15px;
        right: 15px;
      }
    }
  </style>
</head>
<body>
  <!-- Existing CSAT Calculator button -->
  <button class="csat-btn" onclick="openCSATModal()">CSAT Calculator</button>

  <button class="endorsement-btn" onclick="openEndorsementPage()">ENDORSEMENT</button>

  <button class="manual-vi-btn-fixed" onclick="openManualVIPage()">MANUAL-VI</button>

  <!-- New button for Claim_Count & NSTP -->
  <button class="claim-count-nstp-btn-fixed" onclick="openClaimCountNSTPPage()">Claim_Count & NSTP</button>

  <h2 id="mainHeader">📷SHIVANG</h2>
  <div class="upload-section">
    <input type="file" id="fileUpload" accept="image/*">
    <input type="text" id="tagInput" placeholder="Enter tag (e.g., SHIVANG)">
    <button onclick="uploadImage()">Upload</button>
    <div class="progress-container">
      <div class="progress-bar">
        <div class="progress" id="progress">0%</div>
      </div>
      <div class="status" id="status">Ready</div>
    </div>
  </div>

  <h3>Uploaded Images</h3>
  <div id="gallery"></div>

  <div id="tagModal" class="modal">
    <div class="modal-content">
      <h4>Error: Tag is required!</h4>
      <input type="text" id="modalTagInput" placeholder="Enter tag (e.g., SHIVANG)">
      <button class="upload-btn" onclick="submitTag()">Upload</button>
      <button class="cancel-btn" onclick="closeModal()">Cancel</button>
      <div class="modal-progress-container" id="modalProgressContainer">
        <div class="modal-progress-bar">
          <div class="modal-progress" id="modalProgress">0%</div>
        </div>
      </div>
    </div>
  </div>

  <div id="csatModal" class="csat-modal">
    <div class="csat-modal-content">
      <h4>CSAT Calculator</h4>
      <div class="input-section good-section">
        <label>Good Count:</label>
        <input type="number" id="goodCount" min="0" value="0">
      </div>
      <div class="input-section bad-section">
        <label>Bad Count:</label>
        <input type="number" id="badCount" min="0" value="0">
      </div>
      <div class="input-section">
        <label>Required CSAT (%):</label>
        <select id="requiredCSAT">
          <option value="70">70%+</option>
          <option value="71">71%+</option>
          <option value="72">72%+</option>
          <option value="73">73%+</option>
          <option value="74">74%+</option>
          <option value="75">75%+</option>
          <option value="76">76%+</option>
          <option value="77">77%+</option>
          <option value="78">78%+</option>
          <option value="79">79%+</option>
          <option value="80">80%+</option>
          <option value="81">81%+</option>
          <option value="82">82%+</option>
          <option value="83">83%+</option>
          <option value="84">84%+</option>
          <option value="85">85%+</option>
          <option value="86">86%+</option>
          <option value="87">87%+</option>
          <option value="88">88%+</option>
          <option value="89">89%+</option>
          <option value="90">90%+</option>
          <option value="91">91%+</option>
          <option value="92">92%+</option>
          <option value="93">93%+</option>
          <option value="94">94%+</option>
          <option value="95">95%+</option>
          <option value="96">96%+</option>
          <option value="97">97%+</option>
          <option value="98">98%+</option>
          <option value="99">99%+</option>
          <option value="100">100%+</option>
        </select>
      </div>
      <div id="csatResult" class="result-section">
        <p>Total: 0</p>
        <p>CSAT: 0%</p>
        <p id="csatStatus">Enter counts to see status</p>
      </div>
      <div class="button-container">
        <button class="close-btn" onclick="closeCSATModal()">Close</button>
        <button id="calculateButton" class="calculate-btn" onclick="calculateCSAT()">Calculate</button>
      </div>
    </div>
  </div>

  <div id="endorsementPage" class="endorsement-page">
    <div class="endorsement-container">
      <h1>ENDORSEMENT</h1>
      <div class="created-by">Created by Shivang</div>
      <button class="back-btn" onclick="closeEndorsementPage()">Back to Main Page</button>
      <label for="insurer">Select Insurance Company:</label>
      <select id="insurer" class="PB_DROPDOWN">
        <option disabled selected>Select Insurer</option>
      </select>
      <label for="requirement">Select Requirement:</label>
      <select id="requirement" class="PB_DROPDOWN" disabled>
        <option disabled selected>Select Requirement</option>
      </select>
      <div id="output" class="output"></div>
    </div>
  </div>

  <div id="manualVIPage" class="manual-vi-page">
    <button class="back-btn" onclick="closeManualVIPage()">Back to Main Page</button>
    <div class="card mt-4">
      <div class="card-header bg-dark text-white d-flex justify-content-between align-items-center">
        </div>
      <div class="card-body">
        <div class="mb-3 p-3 rounded" style="background-color: #e3f2fd;">
          <strong>ADP Home Visit Cities: 42</strong>
          <ul class="mb-0" style="columns: 2;">
            <li>Aligarh</li><li>Alwar</li><li>Ambala</li><li>Amritsar</li><li>Belgaum</li>
            <li>Bhiwani</li><li>Bhubaneshwar</li><li>Bilaspur</li><li>Coimbatore</li><li>Dhanbad</li>
            <li>Guwahati</li><li>Haldwani</li><li>Haridwar</li><li>Indore</li><li>Jalandhar</li>
            <li>Jamshedpur</li><li>Jhajjar</li><li>Jhansi</li><li>Jind</li><li>Jodhpur</li>
            <li>Kangra</li><li>Madurai</li><li>Mathura</li><li>Moradabad</li><li>Muzaffarnagar</li>
            <li>Mysore</li><li>Nagpur</li><li>Panipat</li><li>Pondicherry</li><li>Raipur</li>
            <li>Rajkot</li><li>Rewa</li><li>Rewari</li><li>Rohtak</li><li>Satara</li>
            <li>Shimla</li><li>Ludhiana</li><li>Surat</li><li>Thiruvananthapuram</li><li>Thrissur</li><li>Udaipur</li>
            <li>Varanasi</li><li>Yamuna Nagar</li>
          </ul>
        </div>
        <div class="mb-3 p-3 rounded" style="background-color: #d0f0c0;">
          <strong>Manual Home Visit Cities: 14</strong>
          <ul class="mb-0" style="columns: 2;">
            <li>Ahmedabad</li><li>Bangalore</li><li>Chennai</li><li>Delhi</li><li>Faridabad</li>
            <li>Ghaziabad</li><li>Gurgaon</li><li>Hyderabad</li><li>Kolkata</li><li>Mumbai</li>
            <li>Noida & Greater Noida</li><li>Patna</li><li>Pune</li><li>Thane & Navi Mumbai</li>
          </ul>
        </div>
      </div>
    </div>
  </div>

  <!-- New Claim_Count & NSTP Section (Insurance Comparison Dashboard) -->
  <div id="claimCountNSTPPage" class="claim-count-nstp-page">
    <div class="container mx-auto p-4 bg-white rounded-2xl shadow-2xl max-w-7xl w-full border-4 border-transparent bg-clip-border bg-gradient-to-r from-blue-500 via-purple-500 to-pink-500" style="margin-top: 20px;">
        <h1 class="text-4xl font-bold text-center mb-6 text-indigo-800 tracking-tight">Insurance Comparison Dashboard</h1>
        <div class="mb-4">
            <input type="text" id="searchInput" placeholder="Search by Insurer Name..." class="search-input w-full p-3 text-lg border-2 border-blue-500 rounded-lg shadow-md focus:outline-none focus:ring-4 focus:ring-pink-500 bg-blue-50 text-gray-800 placeholder-gray-500">
        </div>
        <div class="overflow-x-auto rounded-lg">
            <table id="insuranceTable" class="w-full bg-white border border-gray-300">
                <thead class="bg-gray-900 text-white text-lg font-semibold">
                    <tr>
                        <th class="table-header p-2 text-left" data-column="insurer_name">Insurer Name</th>
                        <!-- Reordered columns: ZD Claims/Year and Non-ZD Claims/Year moved up -->
                        <th class="table-header p-2 text-left" data-column="zd_claims_year">ZD Claims/Year</th>
                        <th class="table-header p-2 text-left" data-column="non_zd_claims_year">Non-ZD Claims/Year</th>
                        <th class="table-header p-2 text-left" data-column="commercial">Commercial</th>
                        <th class="table-header p-2 text-left" data-column="video_approval">Video Approval</th>
                        <th class="table-header p-2 text-left" data-column="video_tat">Video TAT</th>
                        <th class="table-header p-2 text-left" data-column="short_partial">Short Partial</th>
                        <th class="table-header p-2 text-left" data-column="artificial_low_lighting">Artificial Low Lighting</th>
                        <th class="table-header p-2 text-left" data-column="scar_declaration">Scar Declaration</th>
                        <th class="table-header p-2 text-left" data-column="brand_new_3_3">Brand New 3+3</th>
                        <th class="table-header p-2 text-left" data-column="old_3_3">Old 3+3</th>
                    </tr>
                </thead>
                <tbody id="tableBody" class="text-gray-800 text-base">
                    <!-- Data will be populated by JavaScript -->
                </tbody>
            </table>
        </div>
    </div>
    <button class="back-btn" onclick="closeClaimCountNSTPPage()">Back to Main Page</button>
  </div>

  <!-- Chatbox Toggle Button -->
  <button id="chatboxToggleBtn" class="chatbox-toggle-btn">💬</button>

  <!-- Chatbox Container (Full-page overlay) -->
  <div id="chatboxContainer" class="chatbox-container">
    <div class="chatbox-content">
      <div class="chatbox-header">
        <span class="chatbox-title">CHATBOOK</span>
        <span class="chatbox-subtitle">shivang</span>
      </div>
      <div id="chatboxMessages" class="chatbox-messages">
        <!-- Messages will be loaded here by JavaScript -->
      </div>
      <div class="chatbox-input-area">
        <input type="text" id="chatInput" placeholder="Type your message...">
        <button id="sendChatBtn">Send</button>
      </div>
    </div>
  </div>


  <script type="module">
    // Import the functions you need from the SDKs you need
    import { initializeApp } from "https://www.gstatic.com/firebasejs/10.14.1/firebase-app.js";
    import { getDatabase, ref as dbRef, push, onValue, remove, serverTimestamp, get } from "https://www.gstatic.com/firebasejs/10.14.1/firebase-database.js";

    // Your web app's Firebase configuration
    // REPLACE WITH YOUR ACTUAL API KEYS AND PROJECT IDS
    const firebaseConfig = {
      apiKey: "AIzaSyCIfleywEbd1rcjymkfEfFYxPpvYdZHGhk", // Replace with your actual API key
      authDomain: "cvang-vahan.firebaseapp.com",
      databaseURL: "https://cvang-vahan-default-rtdb.firebaseio.com",
      projectId: "cvang-vahan",
      storageBucket: "cvang-vahan.appspot.com",
      messagingSenderId: "117318825099", // Replace with your actual Messaging Sender ID
      appId: "1:117318825099:web:afc0e2f863117cb14bfc" // Replace with your actual App ID
    };

    // Initialize Firebase
    const app = initializeApp(firebaseConfig);
    const db = getDatabase(app);
    const imagesRef = dbRef(db, 'images');

    // Cloudinary configuration
    const cloudName = 'di83mshki'; // Replace with your Cloudinary cloud name
    const uploadPreset = 'anonymous_upload'; // Replace with your Cloudinary upload preset

    // Global variables
    let selectedFile = null;
    let hasCalculated = false;
    let displayedImages = {}; // To keep track of image elements in the gallery for efficient updates

    // --- NEW GLOBAL VARIABLES FOR CHAT ---
    const chatMessagesRef = dbRef(db, 'chatMessages');
    const chatboxToggleBtn = document.getElementById('chatboxToggleBtn');
    const chatboxContainer = document.getElementById('chatboxContainer');
    const chatInput = document.getElementById('chatInput');
    const sendChatBtn = document.getElementById('sendChatBtn');
    const chatboxMessages = document.getElementById('chatboxMessages');

    let anonymousUserId = getAnonymousUserId();
    let replyToMessageId = null; // To store the ID of the message being replied to
    let replyToMessageText = null; // To store a preview of the message being replied to

    // --- CHATBOX FUNCTIONS ---

    // Generates or retrieves a unique anonymous ID for the user
    function getAnonymousUserId() {
        let userId = localStorage.getItem('anonymousUserId');
        if (!userId) {
            // Generate a simple unique ID
            userId = 'anon_' + Math.random().toString(36).substring(2, 9) + Date.now();
            localStorage.setItem('anonymousUserId', userId);
        }
        return userId;
    }

    // Event listeners for chatbox toggle and send
    chatboxToggleBtn.addEventListener('click', () => {
        if (chatboxContainer.style.display === 'flex') {
            chatboxContainer.style.display = 'none';
            showAllMainContent(); // Show main content when closed
        } else {
            chatboxContainer.style.display = 'flex';
            hideAllMainContent(); // Hide main content when chatbox opens
            // Scroll to bottom when opening
            chatboxMessages.scrollTop = chatboxMessages.scrollHeight;
        }
    });

    // Close chatbox when clicking outside the chatbox-content
    chatboxContainer.addEventListener('click', (event) => {
        const chatContent = document.getElementById('chatboxContainer').querySelector('.chatbox-content');
        if (chatContent && !chatContent.contains(event.target)) {
            chatboxContainer.style.display = 'none';
            showAllMainContent(); // Show main content when closed by outside click
        }
    });

    sendChatBtn.addEventListener('click', sendMessage);
    chatInput.addEventListener('keypress', (e) => {
        if (e.key === 'Enter') {
            sendMessage();
        }
    });

    // Function to set the reply context
    window.replyTo = function(messageId, messageText) {
        replyToMessageId = messageId;
        replyToMessageText = messageText;
        chatInput.value = `Replying to "${messageText.substring(0, 30)}${messageText.length > 30 ? '...' : ''}" `;
        chatInput.focus();
    };

    // Sends a message to Firebase Realtime Database
    function sendMessage() {
        const text = chatInput.value.trim();
        if (text) {
            const message = {
                userId: anonymousUserId,
                text: text,
                timestamp: serverTimestamp(),
                parentId: replyToMessageId || null,
                parentText: replyToMessageText || null
            };

            push(chatMessagesRef, message)
                .then(() => {
                    chatInput.value = '';
                    replyToMessageId = null;
                    replyToMessageText = null;
                })
                .catch(error => {
                    console.error("Error sending message:", error);
                    showMessage("Failed to send message.", "error");
                });
        }
    }

    // Define main and reply colors
    const chatColorSchemes = [
        { main: '#1a237e', reply: '#a7b7e5' }, // Blue scheme (Deep Blue for main, Lighter Blue for reply)
        { main: '#ff5722', reply: '#ffddc1' }  // Orange scheme (Deep Orange for main, Lighter Orange for reply)
    ];

    let globalColorAlternatorIndex = 0; // Tracks which main color to use next for non-reply messages

    // Loads and displays chat messages from Firebase
    function loadChatMessages() {
        onValue(chatMessagesRef, (snapshot) => {
            const messagesData = snapshot.val();
            const now = Date.now();
            const fiveDaysInMs = 5 * 24 * 60 * 60 * 1000;

            let currentMessagesArray = [];
            let messagesToDelete = [];

            if (messagesData) {
                Object.entries(messagesData).forEach(([key, msg]) => {
                    const messageTimestamp = msg.timestamp || 0;

                    if (messageTimestamp && (now - messageTimestamp > fiveDaysInMs)) {
                        messagesToDelete.push(key);
                    } else {
                        currentMessagesArray.push({ id: key, ...msg });
                    }
                });

                messagesToDelete.forEach(key => {
                    remove(dbRef(db, `chatMessages/${key}`))
                        .then(() => console.log(`Chat message ${key} deleted (older than 5 days)`))
                        .catch((error) => console.error("Auto-delete chat error:", error));
                });

                // Sort messages by timestamp for display (oldest at top, newest at bottom)
                currentMessagesArray.sort((a, b) => a.timestamp - b.timestamp);
            }

            // Clear previous messages and re-render all to ensure correct order and colors
            chatboxMessages.innerHTML = '';
            globalColorAlternatorIndex = 0; // Reset index for full re-render

            currentMessagesArray.forEach((msg) => {
                const messageElement = document.createElement('div');
                messageElement.dataset.messageId = msg.id;
                messageElement.className = 'chatbox-message';

                let currentColorScheme = null; // This will hold the scheme for the message being rendered
                let parentColorScheme = null;  // This will hold the scheme of the parent message (if reply)
                let alignmentClass = '';
                let appliedBgColor = '';
                let replyBorderColor = '';

                // Determine alignment for the current message
                if (msg.userId === anonymousUserId) {
                    alignmentClass = 'align-right';
                } else {
                    alignmentClass = 'align-left';
                }
                messageElement.classList.add(alignmentClass); // Apply alignment class

                // Determine message background color and reply specific styles
                if (msg.parentId) {
                    // This is a reply
                    messageElement.classList.add('is-reply'); // Add class for reply specific margins/borders

                    // Find the parent message to determine its original color scheme
                    const parentMessage = messagesData[msg.parentId];
                    if (parentMessage) {
                        if (parentMessage.userId === anonymousUserId) {
                            parentColorScheme = chatColorSchemes[0]; // Parent was from current user (Blue scheme)
                        } else {
                            parentColorScheme = chatColorSchemes[1]; // Parent was from another user (Orange scheme)
                        }
                        appliedBgColor = parentColorScheme.reply; // Use parent's lighter reply color
                        replyBorderColor = parentColorScheme.main; // Use parent's dark main color for border
                    } else {
                        // Fallback if parent message is not found (e.g., deleted or old)
                        // Assign a default reply color based on current message sender
                        appliedBgColor = (msg.userId === anonymousUserId) ? chatColorSchemes[0].reply : chatColorSchemes[1].reply;
                        replyBorderColor = (msg.userId === anonymousUserId) ? chatColorScheemes[0].main : chatColorSchemes[1].main;
                    }

                    messageElement.style.backgroundColor = appliedBgColor;
                    if (alignmentClass === 'align-right') {
                        messageElement.style.borderRightColor = replyBorderColor;
                    } else {
                        messageElement.style.borderLeftColor = replyBorderColor;
                    }

                } else {
                    // This is a regular message: use alternating dark colors based on global index
                    const colorIndex = globalColorAlternatorIndex % 2;
                    currentColorScheme = chatColorSchemes[colorIndex];
                    appliedBgColor = currentColorScheme.main; // Get main color from alternating scheme
                    messageElement.style.backgroundColor = appliedBgColor;
                    globalColorAlternatorIndex++; // Increment for the next *non-reply* message
                }

                // Apply reply preview if present, adjust its border color to match the side's main color
                if (msg.parentText) {
                    const replyPreview = document.createElement('span');
                    replyPreview.className = 'reply-text-preview';
                    replyPreview.textContent = `Replying to: "${msg.parentText.substring(0, 40)}${msg.parentText.length > 40 ? '...' : ''}"`;
                    // The border color of the preview should match the main color of the reply's side
                    // If the reply itself is from the current user (align-right)
                    replyPreview.style.borderBottomColor = (alignmentClass === 'align-right') ? chatColorSchemes[0].main : chatColorSchemes[1].main;
                    messageElement.appendChild(replyPreview);
                }

                const messageTextNode = document.createTextNode(msg.text);
                messageElement.appendChild(messageTextNode);

                // Add reply button
                const replyBtn = document.createElement('button');
                replyBtn.className = 'reply-btn';
                replyBtn.textContent = '↩';
                replyBtn.title = 'Reply';
                replyBtn.onclick = () => window.replyTo(msg.id, msg.text);
                messageElement.appendChild(replyBtn);

                chatboxMessages.appendChild(messageElement);
            });

            // Ensure the gallery empty message is shown/hidden correctly
            const gallery = document.getElementById('gallery');
            if (Object.keys(displayedImages).length === 0 && gallery) {
                if (!gallery.querySelector('.no-images-message')) {
                    const noImagesMsg = document.createElement('p');
                    noImagesMsg.className = 'no-images-message';
                    noImagesMsg.style.color = '#455a64';
                    noImagesMsg.style.marginTop = '20px';
                    noImagesMsg.textContent = 'No images uploaded yet.';
                    gallery.appendChild(noImagesMsg);
                }
            } else if (gallery) {
                const noImagesMsg = gallery.querySelector('.no-images-message');
                if (noImagesMsg) {
                    gallery.removeChild(noImagesMsg);
                }
            }

            // Scroll to bottom after all messages are rendered to show the latest message
            chatboxMessages.scrollTop = chatboxMessages.scrollHeight;
        });
    }


    // Expose functions to window object (existing functions)
    window.uploadImage = function() {
      const fileInput = document.getElementById('fileUpload');
      const tagInput = document.getElementById('tagInput');
      const file = fileInput.files[0];
      const tag = tagInput.value.trim();
      const progressBar = document.getElementById('progress');
      const statusText = document.getElementById('status');

      if (!file) {
        showMessage("Please select a file first!", "error");
        return;
      }

      if (!tag) {
        selectedFile = file;
        document.getElementById('tagModal').style.display = 'flex';
        return;
      }

      uploadFile(file, tag, progressBar, statusText);
    };

    window.closeModal = function() {
      document.getElementById('tagModal').style.display = 'none';
      document.getElementById('modalTagInput').value = '';
      document.getElementById('modalProgressContainer').style.display = 'none';
      document.getElementById('modalProgress').style.width = '0%';
      document.getElementById('modalProgress').textContent = '0%';
      document.querySelector('.modal-content .upload-btn').style.display = 'inline-block';
      document.querySelector('.modal-content .cancel-btn').style.display = 'inline-block';
      selectedFile = null;
    };

    window.submitTag = function() {
      const modalTagInput = document.getElementById('modalTagInput');
      const tag = modalTagInput.value.trim();
      const progressBar = document.getElementById('progress');
      const statusText = document.getElementById('status');
      const modalProgress = document.getElementById('modalProgress');
      const modalProgressContainer = document.getElementById('modalProgressContainer');

      if (!tag) {
        showMessage("Tag is required!", "error");
        return;
      }

      modalProgressContainer.style.display = 'block';
      document.querySelector('.modal-content .upload-btn').style.display = 'none';
      document.querySelector('.modal-content .cancel-btn').style.display = 'none';

      uploadFile(selectedFile, tag, progressBar, statusText, modalProgress);
    };

    function uploadFile(file, tag, progressBar, statusText, modalProgress = null) {
      const url = `https://api.cloudinary.com/v1_1/${cloudName}/image/upload`;
      const formData = new FormData();
      formData.append('file', file);
      formData.append('upload_preset', uploadPreset);
      formData.append('tags', tag);

      const xhr = new XMLHttpRequest();

      xhr.upload.onprogress = function(event) {
        if (event.lengthComputable) {
          const percentComplete = Math.round((event.loaded / event.total) * 100);
          progressBar.style.width = percentComplete + '%';
          progressBar.textContent = percentComplete + '%';
          if (modalProgress) {
            modalProgress.style.width = percentComplete + '%';
            modalProgress.textContent = percentComplete + '%';
          }
          statusText.textContent = 'Uploading...';
        }
      };

      xhr.onload = function() {
        if (xhr.status === 200) {
          const data = JSON.parse(xhr.responseText);
          console.log("Cloudinary Response:", data);
          if (!data.secure_url) {
            showMessage('Upload failed: No secure URL received', 'error');
            statusText.textContent = 'Upload failed!';
            closeModal();
            return;
          }
          const imgObj = {
            url: data.secure_url,
            tag: tag,
            name: file.name,
            timestamp: Date.now()
          };
          push(imagesRef, imgObj)
            .then(() => {
              console.log("Firebase Push Successful:", imgObj);
              progressBar.style.width = '100%';
              progressBar.textContent = '100%';
              if (modalProgress) {
                modalProgress.style.width = '100%';
                modalProgress.textContent = '100%';
              }
              statusText.textContent = 'Complete';
              showMessage('Uploaded Successfully!', 'info');
              closeModal();
              document.getElementById('fileUpload').value = '';
              document.getElementById('tagInput').value = '';
            })
            .catch((error) => {
              console.error("Firebase Push Error:", error);
              statusText.textContent = 'Upload failed: Firebase error';
              showMessage('Upload failed: Firebase error', 'error');
              closeModal();
            });
        } else {
          console.error("Cloudinary Upload Failed (HTTP status:", xhr.status, ") Response:", xhr.responseText);
          statusText.textContent = 'Upload failed!';
          showMessage('Upload failed!', 'error');
          closeModal();
        }
      };

      xhr.onerror = function() {
        console.error("Upload error occurred (XHR onerror):", xhr.status);
        statusText.textContent = 'Upload error occurred!';
        showMessage('Upload failed due to a network error!', 'error');
        closeModal();
      };

      xhr.open('POST', url, true);
      xhr.send(formData);
    }

    // Custom message box function (instead of alert)
    function showMessage(message, type = "info") {
      const messageBox = document.createElement("div");
      messageBox.style.position = "fixed";
      messageBox.style.top = "20px";
      messageBox.style.left = "50%";
      messageBox.style.transform = "translateX(-50%)";
      messageBox.style.padding = "15px 25px";
      messageBox.style.borderRadius = "10px";
      messageBox.style.zIndex = "9999";
      messageBox.style.color = "white";
      messageBox.style.fontWeight = "bold";
      messageBox.style.boxShadow = "0 4px 8px rgba(0,0,0,0.2)";
      messageBox.style.transition = "opacity 0.5s ease-in-out";
      messageBox.style.opacity = "1";

      if (type === "error") {
        messageBox.style.backgroundColor = "#f44336";
      } else {
        messageBox.style.backgroundColor = "#4CAF50";
      }

      messageBox.textContent = message;
      document.body.appendChild(messageBox);

      setTimeout(() => {
        messageBox.style.opacity = "0";
        messageBox.addEventListener("transitionend", () => messageBox.remove());
      }, 3000);
    }

    // Function to handle direct image download
    window.downloadImageDirectly = async function(imageUrl, fileName) {
      try {
        const response = await fetch(imageUrl);
        const blob = await response.blob();
        const url = window.URL.createObjectURL(blob);
        const a = document.createElement('a');
        a.style.display = 'none';
        a.href = url;
        a.download = fileName;
        document.body.appendChild(a);
        a.click();
        window.URL.revokeObjectURL(url);
        a.remove();
        showMessage('Download initiated!', 'info');
      } catch (error) {
        console.error("Error downloading image:", error);
        showMessage('Failed to download image.', 'error');
      }
    };

    function loadImages() {
      const gallery = document.getElementById('gallery');

      onValue(imagesRef, (snapshot) => {
        const imagesData = snapshot.val();
        const now = Date.now();
        let currentKeys = {};

        if (imagesData) {
          const sortedImageEntries = Object.entries(imagesData)
            .sort(([, a], [, b]) => (b.timestamp || 0) - (a.timestamp || 0));

          sortedImageEntries.forEach(([key, img]) => {
            currentKeys[key] = true;

            if (now - (img.timestamp || 0) > 300000) {
              if (displayedImages[key]) {
                gallery.removeChild(displayedImages[key]);
                delete displayedImages[key];
              }
              remove(dbRef(db, `images/${key}`))
                .then(() => console.log(`Image ${key} deleted (older than 5 min)`))
                .catch((error) => console.error("Auto-delete error:", error));
            } else {
              if (!displayedImages[key]) {
                const container = document.createElement('div');
                container.className = 'image-container';

                const imgElement = document.createElement('img');
                const optimizedUrl = img.url.replace('/upload/', `/upload/f_auto,q_auto,w_300/`);
                imgElement.src = optimizedUrl;
                imgElement.alt = img.tag || 'Uploaded image';
                imgElement.loading = 'lazy';
                imgElement.onerror = () => {
                  imgElement.src = `https://placehold.co/150x150/cccccc/333333?text=Image+Error`;
                  console.warn(`Failed to load image: ${img.url}`);
                };

                const tagElement = document.createElement('p');
                tagElement.className = 'tag';
                tagElement.textContent = `Tag: ${img.tag || 'No tag'}`;

                const downloadBtn = document.createElement('button');
                downloadBtn.className = 'download-btn';
                downloadBtn.textContent = 'Download';
                downloadBtn.onclick = () => window.downloadImageDirectly(img.url, img.name || `image_${key}.jpg`);

                container.appendChild(imgElement);
                container.appendChild(tagElement);
                container.appendChild(downloadBtn);

                gallery.prepend(container);
                displayedImages[key] = container;
              }
            }
          });
        }

        for (const key in displayedImages) {
          if (!currentKeys[key] && !imagesData[key]) {
            gallery.removeChild(displayedImages[key]);
            delete displayedImages[key];
          }
        }

        if (Object.keys(displayedImages).length === 0) {
          if (!gallery.querySelector('.no-images-message')) {
             const noImagesMsg = document.createElement('p');
             noImagesMsg.className = 'no-images-message';
             noImagesMsg.style.color = '#455a64';
             noImagesMsg.style.marginTop = '20px';
             noImagesMsg.textContent = 'No images uploaded yet.';
             gallery.appendChild(noImagesMsg);
          }
        } else {
            const noImagesMsg = gallery.querySelector('.no-images-message');
            if (noImagesMsg) {
                gallery.removeChild(noImagesMsg);
            }
        }
      });
    }

    // CSAT Calculator Functions
    window.openCSATModal = function() {
      document.getElementById('csatModal').style.display = 'flex';
      hideAllMainContent();
      document.getElementById('endorsementPage').style.display = 'none';
      document.getElementById('manualVIPage').style.display = 'none';
      document.getElementById('claimCountNSTPPage').style.display = 'none';
      calculateCSAT();
    };

    window.closeCSATModal = function() {
      document.getElementById('csatModal').style.display = 'none';
      document.getElementById('goodCount').value = '0';
      document.getElementById('badCount').value = '0';
      document.getElementById('requiredCSAT').value = '70';
      document.getElementById('calculateButton').textContent = 'Calculate';
      hasCalculated = false;
      calculateCSAT();
      showAllMainContent();
    };

    window.calculateCSAT = function() {
      const goodCount = parseInt(document.getElementById('goodCount').value) || 0;
      const badCount = parseInt(document.getElementById('badCount').value) || 0;
      const requiredCSAT = parseInt(document.getElementById('requiredCSAT').value);
      const resultSection = document.getElementById('csatResult');
      const status = document.getElementById('csatStatus');
      const calculateButton = document.getElementById('calculateButton');

      const total = goodCount + badCount;
      const csat = total === 0 ? 0 : (goodCount / total) * 100;
      const formattedCSAT = csat.toFixed(2);

      resultSection.querySelector('p:nth-child(1)').textContent = `Total: ${total}`;
      resultSection.querySelector('p:nth-child(2)').textContent = `CSAT: ${formattedCSAT}%`;

      if (total === 0) {
        status.textContent = 'Enter counts to see status';
        status.className = '';
        return;
      }

      let additionalGoodNeeded = 0;
      let newCSAT = csat;
      let newGoodCount = goodCount;
      let newTotal = total;

      if (csat <= requiredCSAT) {
        while (newCSAT <= requiredCSAT) {
          additionalGoodNeeded++;
          newGoodCount = goodCount + additionalGoodNeeded;
          newTotal = total + additionalGoodNeeded;
          newCSAT = (newGoodCount / newTotal) * 100;
        }
      }

      const exactCSAT = newCSAT;

      const isAboveRequired = csat > requiredCSAT;

      if (isAboveRequired) {
        status.textContent = `Success! CSAT (${formattedCSAT}%) is above required (${requiredCSAT}%+).`;
        status.className = 'success';
      } else {
        status.textContent = `Need ${additionalGoodNeeded} more good count(s) to achieve ${requiredCSAT}%+ (exact: ${exactCSAT.toFixed(2)}%).`;
        status.className = 'error';
      }

      if (!hasCalculated) {
        hasCalculated = true;
        calculateButton.textContent = 'Recalculate';
      }
    };

    window.closeCSATModal = function(event) {
      if (event.target === this || event.currentTarget.classList.contains('close-btn')) {
        document.getElementById('csatModal').style.display = 'none';
        document.getElementById('goodCount').value = '0';
        document.getElementById('badCount').value = '0';
        document.getElementById('requiredCSAT').value = '70';
        document.getElementById('calculateButton').textContent = 'Calculate';
        hasCalculated = false;
        calculateCSAT();
        showAllMainContent();
      }
    };
    document.getElementById('csatModal').addEventListener('click', window.closeCSATModal);


    // ENDORSEMENT Full-Page Functionality
    window.openEndorsementPage = function() {
      document.getElementById('endorsementPage').style.display = 'block';
      setTimeout(() => {
        document.querySelector('.endorsement-container').classList.add('active');
      }, 10);
      hideAllMainContent();
      document.getElementById('csatModal').style.display = 'none';
      document.getElementById('manualVIPage').style.display = 'none';
      document.getElementById('claimCountNSTPPage').style.display = 'none';
    };

    window.closeEndorsementPage = function() {
      document.getElementById('endorsementPage').style.display = 'none';
      document.querySelector('.endorsement-container').classList.remove('active');
      showAllMainContent();
    };

    document.getElementById('endorsementPage').addEventListener('click', function(event) {
      if (event.target === this) {
        closeEndorsementPage();
      }
    });

    // MANUAL-VI Full-Page Functionality
    window.openManualVIPage = function() {
      document.getElementById('manualVIPage').style.display = 'block';
      hideAllMainContent();
      document.getElementById('csatModal').style.display = 'none';
      document.getElementById('endorsementPage').style.display = 'none';
      document.getElementById('claimCountNSTPPage').style.display = 'none';
    };

    window.closeManualVIPage = function() {
      document.getElementById('manualVIPage').style.display = 'none';
      showAllMainContent();
    };

    document.getElementById('manualVIPage').addEventListener('click', function(event) {
      if (event.target === this) {
        closeManualVIPage();
      }
    });

    // New Claim_Count & NSTP Page Functionality
    window.openClaimCountNSTPPage = function() {
      document.getElementById('claimCountNSTPPage').style.display = 'block';
      hideAllMainContent();
      document.getElementById('csatModal').style.display = 'none';
      document.getElementById('endorsementPage').style.display = 'none';
      document.getElementById('manualVIPage').style.display = 'none';
      populateTable(insuranceData);
      setupInsuranceDashboardListeners();
    };

    window.closeClaimCountNSTPPage = function() {
        document.getElementById('claimCountNSTPPage').style.display = 'none';
        showAllMainContent();
    };

    document.getElementById('claimCountNSTPPage').addEventListener('click', function(event) {
      if (event.target === this) {
        if (event.target.classList.contains('claim-count-nstp-page')) {
          closeClaimCountNSTPPage();
        }
      }
    });

    // Helper functions to manage visibility
    function hideAllMainContent() {
      document.getElementById('mainHeader').style.display = 'none';
      document.querySelector('.upload-section').style.display = 'none';
      document.querySelector('h3').style.display = 'none';
      document.getElementById('gallery').style.display = 'none';
      document.querySelector('.csat-btn').style.display = 'none';
      document.querySelector('.endorsement-btn').style.display = 'none';
      document.querySelector('.manual-vi-btn-fixed').style.display = 'none';
      document.querySelector('.claim-count-nstp-btn-fixed').style.display = 'none';
    }

    function showAllMainContent() {
      document.getElementById('mainHeader').style.display = 'block';
      document.querySelector('.upload-section').style.display = 'block';
      document.querySelector('h3').style.display = 'block';
      document.getElementById('gallery').style.display = 'grid';

      const isMobile = window.matchMedia("(max-width: 600px)").matches;
      if (!isMobile) {
        document.querySelector('.csat-btn').style.display = 'block';
        document.querySelector('.endorsement-btn').style.display = 'block';
        document.querySelector('.manual-vi-btn-fixed').style.display = 'block';
        document.querySelector('.claim-count-nstp-btn-fixed').style.display = 'block';
      }
    }

    // Endorsement Data and Logic
    const insurerDropdown = document.querySelector('.endorsement-page #insurer');
    const requirementDropdown = document.querySelector('.endorsement-page #requirement');
    const outputBox = document.querySelector('.endorsement-page #output');

    const endorsementData = [];

    try {
      const insurers = [...new Set(endorsementData.map(d => d["Insurer"]))].sort();
      insurers.forEach(ins => {
        const opt = document.createElement("option");
        opt.value = opt.textContent = ins;
        insurerDropdown.appendChild(opt);
      });
    } catch (error) {
      console.error("Error populating insurers for endorsement:", error);
      showMessage("Error in endorsement JSON data. Please check the syntax and paste valid JSON.", "error");
    }

    insurerDropdown.addEventListener("change", () => {
      requirementDropdown.innerHTML = "<option disabled selected>Select Requirement</option>";
      outputBox.style.display = "none";
      outputBox.classList.remove("show", "output-red");
      const selectedInsurer = insurerDropdown.value;
      const requirements = [...new Set(
        endorsementData.filter(d => d["Insurer"] === selectedInsurer)
            .map(d => d["Requirement"])
      )].sort();
      requirements.forEach(req => {
        const opt = document.createElement("option");
        opt.value = opt.textContent = req;
        requirementDropdown.appendChild(opt);
      });
      requirementDropdown.disabled = false;
    });

    requirementDropdown.addEventListener("change", () => {
      const ins = insurerDropdown.value;
      const req = requirementDropdown.value;
      const record = endorsementData.find(
        d => d["Insurer"] === ins && d["Requirement"] === req
      );
      if (record) {
        outputBox.innerHTML = `
          <div><span class="label">Endorsement Type:</span><span class="value">${record["Endorsement type"]}</span></div>
          <div><span class="label">Documents Required:</span><span class="value">${record["Documents or any other requirement"]}</span></div>
          <div><span class="label">TAT:</span><span class="value">${record["TAT"]}</span></div>
          <div><span class="label">Charges/Deduction:</span><span class="value">${record["Charges / Deduction"]}</span></div>
          <div><span class="label">Inspection:</span><span class="value">${record["Inspection"]}</span></div>
          <div><span class="label">Exception:</span><span class="value">${record["Any Exception"]}</span></div>
          <div><span class="label">Declaration Format:</span><span class="value">${record["Declaration format (if declaration required)"]}</span></div>
        `;
        if (record["Endorsement type"].toLowerCase() === "not possible") {
          outputBox.classList.add("output-red");
        } else {
          outputBox.classList.remove("output-red");
        }
        outputBox.style.display = "block";
        setTimeout(() => outputBox.classList.add("show"), 10);
      }
    });

    // Insurance Comparison Dashboard Data and Logic (from index (4).html)
    const insuranceData = [
        {
            "insurer_name": "National",
            "commercial": "Yes",
            "video_approval": "At PB end",
            "video_tat": "24 Hours",
            "short_partial": "Yes",
            "artificial_low_lighting": "No",
            "scar_declaration": "Declaration Required within Video TAT",
            "zd_claims_year": "ZD Plan: 2, ZD+: Unlimited",
            "non_zd_claims_year": "Unlimited",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "New India Assurance",
            "commercial": "Yes",
            "video_approval": "At PB end",
            "video_tat": "24 Hours",
            "short_partial": "Yes",
            "artificial_low_lighting": "No",
            "scar_declaration": "Declaration Required within Video TAT",
            "zd_claims_year": "2",
            "non_zd_claims_year": "Unlimited",
            "brand_new_3_3": "Yes",
            "old_3_3": "No"
        },
        {
            "insurer_name": "Oriental",
            "commercial": "No",
            "video_approval": "At PB end",
            "video_tat": "24 Hours",
            "short_partial": "No",
            "artificial_low_lighting": "Yes",
            "scar_declaration": "Declaration Required within Video TAT",
            "zd_claims_year": "2",
            "non_zd_claims_year": "Unlimited",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "United India",
            "commercial": "Yes",
            "video_approval": "At PB end",
            "video_tat": "48 Hours",
            "short_partial": "Yes",
            "artificial_low_lighting": "Yes",
            "scar_declaration": "Declaration Required within Video TAT",
            "zd_claims_year": "Unlimited",
            "non_zd_claims_year": "Unlimited",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "Tata AIG",
            "commercial": "Yes",
            "video_approval": "At PB end",
            "video_tat": "2 days",
            "short_partial": "Yes",
            "artificial_low_lighting": "No",
            "scar_declaration": "Declaration Required (with vehicle number) within Video TAT",
            "zd_claims_year": "2",
            "non_zd_claims_year": "Unlimited",
            "brand_new_3_3": "Yes",
            "old_3_3": "Yes"
        },
        {
            "insurer_name": "ICICI Lombard",
            "commercial": "Yes",
            "video_approval": "At PB end",
            "video_tat": "2 days",
            "short_partial": "Yes",
            "artificial_low_lighting": "Yes",
            "scar_declaration": "Declaration Required within Video TAT",
            "zd_claims_year": "2",
            "non_zd_claims_year": "Unlimited",
            "brand_new_3_3": "Yes",
            "old_3_3": "Yes"
        },
        {
            "insurer_name": "Zuno General",
            "commercial": "No",
            "video_approval": "At PB end",
            "video_tat": "2 days",
            "short_partial": "Yes",
            "artificial_low_lighting": "No",
            "scar_declaration": "Declaration Required within Video TAT",
            "zd_claims_year": "2",
            "non_zd_claims_year": "Unlimited",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "Cholamandalam MS",
            "commercial": "No",
            "video_approval": "At PB end",
            "video_tat": "2 days",
            "short_partial": "Yes",
            "artificial_low_lighting": "No",
            "scar_declaration": "Will Not Accept Scar on WS/change insurer",
            "zd_claims_year": "2",
            "non_zd_claims_year": "Unlimited",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "Future Generali",
            "commercial": "No",
            "video_approval": "At PB end",
            "video_tat": "2 days",
            "short_partial": "Yes",
            "artificial_low_lighting": "No",
            "scar_declaration": "Declaration Required within Video TAT",
            "zd_claims_year": "2",
            "non_zd_claims_year": "Unlimited",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "MAGMA",
            "commercial": "No",
            "video_approval": "At PB end",
            "video_tat": "2 days",
            "short_partial": "Yes",
            "artificial_low_lighting": "No",
            "scar_declaration": "Declaration Required (Scar on Driver Side not accepted) within Video TAT",
            "zd_claims_year": "Unlimited",
            "non_zd_claims_year": "Unlimited",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "Raheja QBE",
            "commercial": "No",
            "video_approval": "At PB end",
            "video_tat": "2 days",
            "short_partial": "Yes",
            "artificial_low_lighting": "No",
            "scar_declaration": "Declaration Required within Video TAT",
            "zd_claims_year": "2",
            "non_zd_claims_year": "Unlimited",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "Kotak",
            "commercial": "No",
            "video_approval": "At PB end",
            "video_tat": "2 days",
            "short_partial": "Yes",
            "artificial_low_lighting": "No",
            "scar_declaration": "Declaration Required within Video TAT",
            "zd_claims_year": "2",
            "non_zd_claims_year": "Unlimited",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "SBI General",
            "commercial": "Yes",
            "video_approval": "At PB end",
            "video_tat": "2 days",
            "short_partial": "Yes",
            "artificial_low_lighting": "No",
            "scar_declaration": "Declaration Required within Video TAT",
            "zd_claims_year": "Unlimited",
            "non_zd_claims_year": "Unlimited",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "Shriram",
            "commercial": "Yes",
            "video_approval": "At PB end",
            "video_tat": "2 days",
            "short_partial": "Yes",
            "artificial_low_lighting": "No",
            "scar_declaration": "Declaration Required (Shriram format) + Address ID proof within Video TAT",
            "zd_claims_year": "2",
            "non_zd_claims_year": "Unlimited till IDV",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "Iffco Tokio",
            "commercial": "No",
            "video_approval": "At PB end",
            "video_tat": "2 days",
            "short_partial": "Yes",
            "artificial_low_lighting": "No",
            "scar_declaration": "Declaration Required within Video TAT",
            "zd_claims_year": "Unlimited",
            "non_zd_claims_year": "Unlimited",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "Liberty Videocon",
            "commercial": "No",
            "video_approval": "At PB end",
            "video_tat": "2 days",
            "short_partial": "No",
            "artificial_low_lighting": "No",
            "scar_declaration": "Will Not Accept Scar on WS/change insurer",
            "zd_claims_year": "Unlimited",
            "non_zd_claims_year": "Unlimited",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "HDFC Ergo",
            "commercial": "No",
            "video_approval": "At PB end",
            "video_tat": "2 days",
            "short_partial": "Yes",
            "artificial_low_lighting": "No",
            "scar_declaration": "Will Not Accept Scar on WS/change insurer",
            "zd_claims_year": "2",
            "non_zd_claims_year": "Unlimited",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "Reliance",
            "commercial": "Yes",
            "video_approval": "At PB end",
            "video_tat": "2 days",
            "short_partial": "Yes",
            "artificial_low_lighting": "No",
            "scar_declaration": "Declaration Required (with vehicle number) within Video TAT",
            "zd_claims_year": "2",
            "non_zd_claims_year": "Unlimited till IDV",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "Bajaj Allianz",
            "commercial": "Yes",
            "video_approval": "At U/W end",
            "video_tat": "2 days",
            "short_partial": "Yes",
            "artificial_low_lighting": "No",
            "scar_declaration": "Will Refer to Under Writer",
            "zd_claims_year": "2",
            "non_zd_claims_year": "Unlimited",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "Royal Sundaram",
            "commercial": "No",
            "video_approval": "At U/W end",
            "video_tat": "2 days",
            "short_partial": "No",
            "artificial_low_lighting": "No",
            "scar_declaration": "Will Refer to Under Writer",
            "zd_claims_year": "Unlimited till IDV",
            "non_zd_claims_year": "Unlimited till IDV",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "Universal Sompo",
            "commercial": "No",
            "video_approval": "At U/W end",
            "video_tat": "2 days",
            "short_partial": "No",
            "artificial_low_lighting": "No",
            "scar_declaration": "Will Refer to Under Writer",
            "zd_claims_year": "Unlimited till IDV",
            "non_zd_claims_year": "Unlimited till IDV",
            "brand_new_3_3": "No",
            "old_3_3": "No"
        },
        {
            "insurer_name": "Digit",
            "commercial": "Yes",
            "video_approval": "At PB end",
            "video_tat": "2 days",
            "short_partial": "No",
            "artificial_low_lighting": "No",
            "scar_declaration": "Declaration Required within Video TAT",
            "zd_claims_year": "1 or 2 claims (as per selected plan)",
            "non_zd_claims_year": "Unlimited till IDV",
            "brand_new_3_3": "Yes",
            "old_3_3": "Yes"
        }
    ];

    function populateTable(data) {
        const tableBody = document.getElementById('tableBody');
        tableBody.innerHTML = '';
        data.forEach(item => {
            const row = document.createElement('tr');
            row.className = 'table-row border-b';
            row.innerHTML = `
                <td class="p-2 font-medium text-indigo-900">${item.insurer_name}</td>
                <td class="p-2">${item.zd_claims_year}</td>
                <td class="p-2">${item.non_zd_claims_year}</td>
                <td class="p-2 ${item.commercial === 'Yes' ? 'text-green-700' : 'text-red-700'}">${item.commercial}</td>
                <td class="p-2">${item.video_approval}</td>
                <td class="p-2">${item.video_tat}</td>
                <td class="p-2 ${item.short_partial === 'Yes' ? 'text-green-700' : 'text-red-700'}">${item.short_partial}</td>
                <td class="p-2 ${item.artificial_low_lighting === 'Yes' ? 'text-green-700' : 'text-red-700'}">${item.artificial_low_lighting}</td>
                <td class="p-2">${item.scar_declaration}</td>
                <td class="p-2 ${item.brand_new_3_3 === 'Yes' ? 'text-green-700' : 'text-red-700'}">${item.brand_new_3_3}</td>
                <td class="p-2 ${item.old_3_3 === 'Yes' ? 'text-green-700' : 'text-red-700'}">${item.old_3_3}</td>
            `;
            tableBody.appendChild(row);
        });
    }

    function sortTable(column, order) {
        const sortedData = [...insuranceData].sort((a, b) => {
            const aValue = String(a[column]).toLowerCase();
            const bValue = String(b[column]).toLowerCase();

            if (order === 'asc') {
                return aValue > bValue ? 1 : -1;
            } else {
                return aValue < bValue ? 1 : -1;
            }
        });
        populateTable(sortedData);
    }

    function setupInsuranceDashboardListeners() {
        const tableHeaders = document.querySelectorAll('#insuranceTable .table-header');
        tableHeaders.forEach(header => {
            const newHeader = header.cloneNode(true);
            header.parentNode.replaceChild(newHeader, header);
        });

        document.querySelectorAll('#insuranceTable .table-header').forEach(header => {
            header.addEventListener('click', () => {
                const column = header.dataset.column;
                const currentOrder = header.classList.contains('sort-asc') ? 'desc' : 'asc';

                document.querySelectorAll('#insuranceTable .table-header').forEach(h => {
                    h.classList.remove('sort-asc', 'sort-desc');
                    h.classList.add('sort-icon');
                });

                header.classList.remove('sort-icon');
                header.classList.add(currentOrder === 'asc' ? 'sort-asc' : 'sort-desc');

                sortTable(column, currentOrder);
            });
        });

        const searchInput = document.getElementById('searchInput');
        if (searchInput) {
            const newSearchInput = searchInput.cloneNode(true);
            searchInput.parentNode.replaceChild(newSearchInput, searchInput);

            newSearchInput.addEventListener('input', (e) => {
                const searchTerm = e.target.value.toLowerCase();
                const filteredData = insuranceData.filter(item =>
                    item.insurer_name.toLowerCase().includes(searchTerm)
                );
                populateTable(filteredData);
            });
        }
    }

    // Initial load of images when the page loads
    loadImages();
    // Initial load of chat messages
    loadChatMessages();

  </script>
</body>
</html>
