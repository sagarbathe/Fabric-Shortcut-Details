# Fabric-Shortcut-Details

Currently, there is no way in Fabric to show details of all the shortcuts created in workspaces and lakehouses. The objective of this project is to capture this information via the Fabric Shortcut REST APIs and use Power BI to visualize this information

This repo will consist of a notebook and Power BI report sample. The notebook captures metadata about all the shortcuts across all lakehouses and workspaces in your Fabric tenant. 

Prerquisites:
- Please ensure all capacities in your Fabric tenant are running before you run the notebook. Once the notebook is executed successfully, capacities can be paused (except the one where the Power BI report will use)
- Currently, the Shortcuts API (List Shortcuts) does not support Service Principal or Managed identities. So a user idnentity is needed to run the notebook. See more details here (https://learn.microsoft.com/en-us/rest/api/fabric/core/onelake-shortcuts/list-shortcuts?tabs=HTTP)
- It is advisable to run the notebook as Fabric Admin user since the shortcut API does not support service principal at this time


Steps:

- Import the notebook 'GetFabricShortcuts.ipynb' in the workspace of your choice.
- Follow all the instructions in the notebook. After successful completion of the notebook, a delta table called 'ShortcutsMetadata' will be created in the lakehouse you had specified in the notebook
- Create a custom semantic model (dataset) called 'sm_ShortcutsMetadata' in the lakehouse you had selected in the notebook. Include the table 'ShortcutsMetadata' in the semantic model
- Import the Power BI report 'Fabric Workspace Shortcut Details' in Power BI desktop. Ensure you are logged in as same user as in Fabric. You should see a pop-up that report is not able to find the dataset. Click on Edit and select semantic model (dataset) created 
  in the previous step. Save and publish the report in the workspace you saved the notebook and semantic model earlier. Now you should be able to open the report in Fabric and use it

PowerBI Report screenshots:

![image](https://github.com/user-attachments/assets/b77d7f89-1ecb-42ee-90b1-89443e4282f1)

![image](https://github.com/user-attachments/assets/0f761ad5-56df-4d5a-916d-f32b08a7b00c)

